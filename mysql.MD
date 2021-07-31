MariaDB [(none)]> create database college;
Query OK, 1 row affected (0.000 sec)

MariaDB [(none)]> use college;
Database changed
MariaDB [college]> CREATE TABLE Students( roll int, name  varchar(255), email varchar(255));
Query OK, 0 rows affected (0.315 sec)

MariaDB [college]> CREATE TABLE Ranks( roll int, rank int);
Query OK, 0 rows affected (0.236 sec)



MariaDB [college]> show tables;
+-------------------+
| Tables_in_college |
+-------------------+
| Ranks             |
| Students          |
+-------------------+
2 rows in set (0.000 sec)

MariaDB [college]> desc Students;
+-------+--------------+------+-----+---------+-------+
| Field | Type         | Null | Key | Default | Extra |
+-------+--------------+------+-----+---------+-------+
| roll  | int(11)      | YES  |     | NULL    |       |
| name  | varchar(255) | YES  |     | NULL    |       |
| email | varchar(255) | YES  |     | NULL    |       |
+-------+--------------+------+-----+---------+-------+
3 rows in set (0.001 sec)


MariaDB [college]> INSERT INTO Students (roll,name,email) VALUES (1, "vinod", "vinod@gmail.com"),(2,"Dev","dev@gmail.com");
Query OK, 2 rows affected (0.043 sec)
Records: 2  Duplicates: 0  Warnings: 0

MariaDB [college]> select * from Students; 
+------+-------+-----------------+
| roll | name  | email           |
+------+-------+-----------------+
|    1 | vinod | vinod@gmail.com |
|    2 | Dev   | dev@gmail.com   |
+------+-------+-----------------+
2 rows in set (0.000 sec)

MariaDB [college]> select * from Students where roll=1; 
+------+-------+-----------------+
| roll | name  | email           |
+------+-------+-----------------+
|    1 | vinod | vinod@gmail.com |
+------+-------+-----------------+
1 row in set (0.000 sec)

MariaDB [college]> describe Ranks;
+-------+---------+------+-----+---------+-------+
| Field | Type    | Null | Key | Default | Extra |
+-------+---------+------+-----+---------+-------+
| roll  | int(11) | YES  |     | NULL    |       |
| rank  | int(11) | YES  |     | NULL    |       |
+-------+---------+------+-----+---------+-------+
2 rows in set (0.001 sec)

MariaDB [college]> INSERT INTO Ranks (roll,rank) VALUES (1, 56),(2,57);
Query OK, 2 rows affected (0.074 sec)
Records: 2  Duplicates: 0  Warnings: 0

MariaDB [college]> select * from Ranks;
+------+------+
| roll | rank |
+------+------+
|    1 |   56 |
|    2 |   57 |
+------+------+
2 rows in set (0.000 sec)


MariaDB [college]> select s.roll, name , rank from Students s join Ranks r on s.roll = r.roll;
+------+-------+------+
| roll | name  | rank |
+------+-------+------+
|    1 | vinod |   56 |
|    2 | Dev   |   57 |
+------+-------+------+
2 rows in set (0.001 sec)
