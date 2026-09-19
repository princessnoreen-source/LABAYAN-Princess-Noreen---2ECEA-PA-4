## PROGRAMMING ASSIGNMENT #4
### by: LABAYAN, Princess Noreen - 2ECEA

This repository is a partial requirement for ECE 2112 "Advanced Computer Programming and Algorithms" as Programming Assignment #3. Its objective is to demonstrate the use of the Pandas library for data wrangling and the Matplotlib library for data visualization through filtering, grouping, and graphical representation of student data.

## A. VISAYAS COMMUNICATION DATAFRAME

The goal of this problem is to create a DataFrame containing students whose hometown is Visayas and whose track is Communication. The resulting DataFrame displays only the Name, Gender, Math, Electronics, and Average columns.

Following were the operators used to execute the code:

1. ```pd.read_csv("filename.csv")```

   This function reads a CSV file and stores its contents as a Pandas DataFrame.

Example:

```python
df = pd.read_csv("board2.csv")
```

2. ```DataFrame[(condition1) & (condition2)]```

   This operator filters the rows of a DataFrame using multiple conditions. The symbol `&` represents the logical "AND" operator.

Example:

```python
df[(df["Hometown"] == "Visayas") & (df["Track"] == "Communication")]
```

3. ```DataFrame[[column1, column2, ...]]```

   This operator selects only the specified columns from a DataFrame.

Example:

```python
df[["Name", "Gender", "Average"]]
```

4. ```len(variable_name)```

   This function returns the number of rows contained in the DataFrame.

Example:

```python
len(VisComm)
```

Using the operators discussed above, the code below was created to display all Communication students from Visayas together with their corresponding information.

```python
VisComm = df[(df["Hometown"] == "Visayas") & (df["Track"] == "Communication")][["Name", "Gender", "Math", "Electronics", "Average"]]

print(VisComm)
print("\n Number of rows:", len(VisComm))
```

---

## B. VISAYAS FEMALE DATAFRAME

The goal of this problem is to create a DataFrame containing female students from Visayas and display only those whose Average grade is greater than or equal to 60.

Following were the operators used to execute the code:

1. ```DataFrame[(condition1) & (condition2)]```

   This operator filters rows using multiple conditions.

Example:

```python
df[(df["Hometown"] == "Visayas") & (df["Gender"] == "Female")]
```

2. ```DataFrame[DataFrame["column"] >= value]```

   This operator filters rows whose values satisfy a numerical condition.

Example:

```python
VisFemale[VisFemale["Average"] >= 60]
```

Using the operators discussed above, the code below was created to display all female students from Visayas and identify those with an Average grade of at least 60.

```python
VisFemale = df[
    (df["Hometown"] == "Visayas") &
    (df["Gender"] == "Female")
][["Name", "Track", "GEAS", "Electronics", "Average"]]

print(VisFemale)

print("\n Students with Average >= 60 \n")
print(VisFemale[VisFemale["Average"] >= 60])
```

---

## C. DATA VISUALIZATION

The goal of this problem is to compute the sample mean of the students' Average grades according to Track, Gender, and Hometown, then present the results using bar graphs.

Following were the operators used to execute the code:

1. ```DataFrame.groupby("column")```

   This function groups the rows of a DataFrame according to the values of a specified column.

Example:

```python
df.groupby("Track")
```

2. ```mean()```

   This function computes the average of the selected numerical values.

Example:

```python
df.groupby("Track")["Average"].mean()
```

3. ```plt.bar(x, y)```

   This function creates a bar graph using the specified x-axis and y-axis values.

Example:

```python
plt.bar(track_mean.index, track_mean.values)
```

4. ```plt.title()```, ```plt.xlabel()```, ```plt.ylabel()```

   These functions add a title and labels to the graph for better presentation.

Example:

```python
plt.title("Average by Track")
plt.xlabel("Track")
plt.ylabel("Average")
```

5. ```idxmax()```

   This function returns the index label corresponding to the highest value in a Series.

Example:

```python
track_mean.idxmax()
```

Using the operators discussed above, the code below was created to compute the sample means, visualize the results using bar graphs, and identify the category with the highest sample mean Average.

```python
track_mean = df.groupby('Track')['Average'].mean().reset_index()
gender_mean = df.groupby('Gender')['Average'].mean().reset_index()
hometown_mean = df.groupby('Hometown')['Average'].mean().reset_index()

print("\nMean Average by Track")
display(track_mean)
print("\nMean Average by Gender")
display(gender_mean)
print("\nMean Average by Hometown")
display(hometown_mean)

track_mean = df.groupby("Track")["Average"].mean()
gender_mean = df.groupby("Gender")["Average"].mean()
hometown_mean = df.groupby("Hometown")["Average"].mean()

plt.figure(figsize=(18,5))


plt.subplot(1,3,1)
plt.bar(track_mean.index, track_mean.values)
plt.title("Average by Track")
plt.xlabel("Track")
plt.ylabel("Average")


plt.subplot(1,3,2)
plt.bar(gender_mean.index, gender_mean.values)
plt.title("Average by Gender")
plt.xlabel("Gender")
plt.ylabel("Average")


plt.subplot(1,3,3)
plt.bar(hometown_mean.index, hometown_mean.values)
plt.title("Average by Hometown")
plt.xlabel("Hometown")
plt.ylabel("Average")

plt.tight_layout()
plt.show()

print("The ", track_mean.idxmax(), "track obtained the highest sample mean Average.")
print( gender_mean.idxmax(), "students obtained the highest sample mean Average.")
print("Students from ", hometown_mean.idxmax(), "obtained the highest sample mean Average.")
```

Thank youuu for reading! <3
