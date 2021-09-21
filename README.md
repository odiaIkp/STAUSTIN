CREATE DATABASE MICHAELA;
USE MICHAELA;
select* from crime;

## to find the area that has the highest cases of theft 
##303W 15TH STAUSTIN(4),408W 15TH STAUSTIN(6), 303W 15TH STAUSTIN(29) so therefore, 15TH STAUSTIN has 39 theft cases during the year 2015 making it the highest
select
location,
count(primary_type)as number_of_theft_cases,
year
from theft1
group by location;

## 601E 15TH STAUSTIN(20),408W 15TH STAUSTIN(9) so , 15TH STAUSTIN has 29 theft cases in 2016 making it the highest location for theft cases
select
location,
count(primary_type)as number_of_theft_cases,
year
from theft2
group by location;

create temporary table theft2
select* 
from clean
where year=2016;

## find out the location with the highest theft case in uk
create temporary table theft1
select* 
from clean
where year=2015;

## clean my new table michaela to remove duplicates
create temporary table clean
select
distinct unique_key,location,
primary_type,
year
from Michaela

## arranging my table to be meaningful by taking the columns needed for my analysis
create temporary table Michaela
select
unique_key,
concat(address,' ',district) as location,
primary_type,
year
from crime
where primary_type ='Theft'
order by primary_type asc;
