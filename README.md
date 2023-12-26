My SQL Note
---------------------------

Roll , Name Gender, Age, GPA, City

//Show Databases
SHOW DATABASES

// Create Database
CREATE DATABASE

// Create Table
CREATE TABLE student
   (
	Roll int,
	Name varchar(15),
	Gender varchar(10),
	Age int,
	GPA double(3,2),
	City varchar(20),
	PRIMARY KEY(Roll)
   );



// Rename Table
RENAME TABLE old_name TO new_name;


// Drop Table
DROP TABLE table name;


// Insert Table Value
INSERT INTO student_details
(Roll, Name, Gender, Age, GPA, City)
VALUES(101, 'Sakib', 'Male', 21, 3.13, 'Sylhet');



// Another System : Insert Table Value
INSERT INTO student_details
VALUES
(101, 'Sakib', 'Male', 21, 3.13, 'Sylhet'),
(102, 'Sakib', 'Male', 21, 3.13, 'Sylhet'),
(103, 'Sakib', 'Male', 21, 3.13, 'Sylhet'),
(104, 'Sakib', 'Male', 21, 3.13, 'Sylhet');


// For search column
SELECT Name
FROM student_details;


// Data search Double name remove and show single
SELECT DISTINCT City
FROM student_details;


//For limited data search and show
SELECT *
FROM student_details
LIMIT 5;
LIMIT 2,5(For first two data remove and show 5 data)


//From small to big order
SELECT Name
FROM student_details
ORDER BY Name;


////From big  to small order
SELECT Roll, Name, City
FROM student_details
ORDER BY Name DESC;


// Between
SELECT Roll, Name, GPA
FROM student_details
WHERE Roll BETWEEN 102 AND 105;


// Where, OR, AND, OPERATOR
SELECT *
FROM student_details
WHERE City = 'Sylhet'
      AND
(Gender = 'Female' OR GPA >= 3.50);


// OR vs IN
SELECT * 
FROM student_details 
WHERE City = 'Sylhet'
OR 
City = 'Khulna' 
OR 
City = 'Sylhet';

SELECT * 
FROM student_details 
WHERE City IN ('Sylhet', 'Khulna', 'Sylhet');


// Like Logical operator
SELECT * 
FROM student_details 
WHERE Name LIKE 'S%';

SELECT * 
FROM student_details 
WHERE Name LIKE '%S';

SELECT * 
FROM student_details 
WHERE Name LIKE '_i%';

SELECT * 
FROM student_details 
WHERE Name LIKE '%i%';



// AS Keywords for Custom name 
SELECT Roll AS ID, Name AS 'First Name'
FROM student_details;

// For Data delete
DELETE FROM teacher
WHERE ID = 105;


//Update data 
UPDATE teacher
SET Salary = Salary + 5000
WHERE Salary = Salary > 10000;


// UPPER and LOWER
SELECT LOWER('I AM NAZMUS SAKIB kabbo')
SELECT UPPER('I AM NAZMUS SAKIB kabbo')


//CONCAT
SELECT CONCAT ('Welcome to', ' New channel');

SELECT CONCAT (Name, ' is ', Age, ' Years old ') AS student_details
FROM student_details;

//GREAREST / LEAST
SELECT GREATEST(12, 56, 43);
SELECT LEAST(12, 56, 43);


// POWER / LOG
SELECT POW(2,3);
SELECT LOG(2)


//TRUNCATE FUNCTION
SELECT TRUNCATE (LOG(2),2);

// MAX / MIN FUNCTION
SELECT MIN(GPA)
FROM student_details;

// SUM & AVG FUNCTION
SELECT SUM(Salary), AVG(Salary)
FROM teacher;

//


SELECT *
FROM student_details
WHERE Gender= 'Female' AND GPA = (SELECT MIN(GPA) FROM student_details);


//Sub Query
SELECT * 
FROM teacher
WHERE Salary > (SELECT AVG(Salary) FROM teacher);


// ALTER Statement for add new collum
ALTER TABLE teacher
ADD Age int(5);

// Rename column name by Alter Statement
ALTER TABLE teacher
CHANGE dept Department varchar(15);

// For delete column 
ALTER TABLE teacher
DROP Column Age;

// for value update
UPDATE teacher
SET Department='CSE'
WHERE ID=100;


//Group By Clouse
SELECT Department SUM(Salary)
FROM teacher
GROUP BY Department;


//ORDER BY Statement
SELECT Department, SUM(Salary)
FROM teacher
GROUP BY Department
ORDER BY SUM(Salary) DESC;

//Remove table data byTRUNCATE TABLE Command in SQL
TRUNCATE TABLE teacher;


// Create Table 
CREATE TABLE students_details
(
    Roll int NOT NULL AUTO_INCREMENT,
    Name varchar (15) NOT NULL,
    Gender varchar (10),
    Age int,
    PRIMARY KEY (Roll)
);


//Inset table values
INSERT INTO students_details(Roll, Name, Gender, Age)
VALUES
(101, 'Rahim', 'Male', 18);


INSERT INTO students_details(Name, Gender, Age)
VALUES
('Rahim', 'Male', 18),
('Farjana', 'Female', 17),
('Mahfuz', 'Male', 18),
('Farhana', 'Female', 17)


//Join with 2 tables
SELECT students_details.Roll, Reg_Number, Name, Gender, Group_Name, GPA
FROM students_details, exam_results
WHERE students_details.Roll = exam_results.Roll;

SELECT students_details.Roll, exam_results.Reg_Number, students_details.Name, students_details.Gender, exam_results.Group_Name, exam_results.GPA
FROM students_details, exam_results
WHERE students_details.Roll = exam_results.Roll;


// USE of Join Clouse 
SELECT students_details.Roll, exam_results.Reg_Number, students_details.Name, students_details.Gender, exam_results.Group_Name, exam_results.GPA
FROM students_details JOIN exam_results
ON students_details.Roll = exam_results.Roll;


// Two table by INNER JOIN
SELECT std.Roll, exam.Reg_Number, std.Name, std.Gender, exam.GPA, exam.Group_Name
FROM students_details AS std INNER JOIN exam_results AS exam
ON std.Roll = exam.Roll;


// Left join in two table
SELECT std.Roll, exam.Reg_Number, std.Name, std.Gender, exam.GPA, exam.Group_Name
FROM students_details AS std LEFT JOIN exam_results AS exam
ON std.Roll = exam.Roll;


// Right join in two table
SELECT std.Roll, exam.Reg_Number, std.Name, std.Gender, exam.GPA, exam.Group_Name
FROM students_details AS std RIGHT JOIN exam_results AS exam
ON std.Roll = exam.Roll;


// Create table
CREATE TABLE Study_Tour
(
  Roll int,
  Name varchar (15),
  Gender varchar (15),
  Age int

);


// UNION & UNION All
SELECT Roll, Name, Gender, Age
FROM dhaka_tour

UNION ALL

SELECT Roll, Name, Gender, Age
FROM sylhet_tour;


// MYSql go
Key - Alt+Enter


// Create virtual table view from real table
CREATE VIEW students_view AS
SELECT Roll, Name, Gender
FROM students_details 

// Show virtual table
SELECT *
FROM students_view;


//ADD DATE FUNCTION
SELECT ADDDATE('2023-10-2', INTERVAL 5 DAY);
SELECT ADDDATE('2023-10-2', INTERVAL 5 MONTH);


//SUB DATE FUNCTION
SELECT SUBDATE('2023-10-2', INTERVAL 5 MONTH);


//MAKE DATE
SELECT MAKEDATE(2018,212)


//DAY NAME
SELECT DAYNAME('2023-10-02');

//MONTH NAME
SELECT MONTHNAME('2023-10-02');


// Delete column from table
ALTER TABLE table_name
DROP COLUMN column_name

ALTER TABLE students_details
DROP COLUMN DOB;



