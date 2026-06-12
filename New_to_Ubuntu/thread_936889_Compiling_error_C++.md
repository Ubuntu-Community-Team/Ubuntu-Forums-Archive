---
title: "Compiling error C++"
date: 2008-10-03
forum: New to Ubuntu
---

### Post by C++beginner on 2008-10-03
Hi,

I get errors when i compile the program to calculate the number of days between two given dates. I am not able to figure out how to correct them.. Pls help..



#include<iostream>
#include<fstream>
#include<cstdlib>
#include<cctype>
#include<cmath>
#include<string>
#include<cstring>
#include<iomanip>
using namespace std;


class Date
{

private:
    int month;
    int day;
    int year;

public:
    
    
    Date(int mm, int dd, int yy);            
    Date( ){month=1; day=1; year=1900;}                
    
    int GetDay();
    int GetMonth();
    int GetYear();
    
    void set_date(int mm, int dd, int yy);    
    void display_date();                    
                            
    bool is_equal(Date& );
    bool is_less_than(Date& );
    
    void advance();                            



};

int difference(Date date1, Date date2);
int main()
{

int m1, m2, d1, d2, y1, y2, index=0;
int mm1, mm2, dd1, dd2, yy1, yy2, days_apart;
char slash;
Date First_Date, Second_Date, earlier_date, later_date;

cout<<"This program gives the number of days between two dates."<<endl;


cout<<"Please enter a date in the form xx/xx/xxxx"<<endl;
cout<<"please enter the date today separated by the forward slash key(e.g 12/08/2004)\n";
cin>>m1>>slash>>d1>>y1;

First_Date.set_date(m1, d1, y1);

cout<<"First Date is:"<<endl;
First_Date.display_date();
cout<<endl;

cout<<"Please enter a second date in the form xx/xx/xxxx"<<endl;

cin>>m2>>slash>>d2>>y2;
Second_Date.set_date(m2, d2, y2);

cout<<"Second Date is:"<<endl;
Second_Date.display_date();
cout<<endl;

if(First_Date.is_equal(Second_Date))
{
    cout<<"The first date you entered is the same as the second date."<<endl;
    
}

else if(First_Date.is_less_than(Second_Date))

{
    
    earlier_date=First_Date;        
    later_date=Second_Date;
    
    cout<<"The first date you entered is earlier than the second date."<<endl;


    dd1=d1;
    mm1=m1;
    yy1=y1;
    
    dd2=d2;
    mm2=m2;
    yy2=y2;
    
}

else
{    
    cout<<"The first date you entered is later than the second date"<<endl;
    
    earlier_date=Second_Date;
    later_date=First_Date;
    

    dd1=d2;
    mm1=m2;
    yy1=y2;
    
    dd2=d1;
    mm2=m1;
    yy2=y1;

}

days_apart= difference(earlier_date, later_date);
cout<<"The two days are "<< days_apart<<" days apart."<<endl;


return 0;
}



int difference(Date date1, Date date2)
{

int diff_days=0;

while ((earlier_day!=later_day)|| (earlier_month!=later_month) || (earlier_year!=later_year))

{
    date1.advance();
    diff_days++;
}
return diff_days;

}


void Date::advance()

{
    
int months[12],td,tm,ty;

int max_no_months=12;

int days_in_month[12]={31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31};

 td = date1.day;
 tm = date1.month;
 ty=date1.year;
 td++;
 if ( td > days_in_month[tm-1])
 {
   td=1;
   tm++;
   if ( tm > 12 )
   { ty++; tm=1; }

 }

return;

}


int Date::GetMonth()
{

return month;
}


int Date::GetDay()
{
return day;
}

int Date::GetYear()
{
return year;
}


void Date::set_date(int mm, int dd, int yy)
{    
month = mm;
day = dd;
year = yy;

}

void Date::display_date()
{    

string name_of_month[12];

name_of_month[0]="January";
name_of_month[1]= "February";
name_of_month[2]= "March";
name_of_month[3]= "April";
name_of_month[4]=  "May";
name_of_month[5]= "June";
name_of_month[6]= "July";
name_of_month[7]= "August";
name_of_month[8]= "September";
name_of_month[9]= "October";
name_of_month[10]= "November";
name_of_month[11]= "December";

cout <<  name_of_month[month-1]  <<  " "  <<  day  <<  ", "  <<   year;
return;
}

bool Date::is_equal(Date& Second_Date)
{

if ((month==Second_Date.month) && (day==Second_Date.day) && (year==Second_Date.year))
    {return true;}

else
    {return false;}
}

bool Date::is_less_than(Date& Second_Date)
{

if (year<Second_Date.year)
{
    return true;
}

else if (month< Second_Date.month)
{
    return true;
}
else if (day<Second_Date.day)
{    
    return true;
}

else
{    
    return false;
}    
}

---

### Post by vlc on 2008-10-03
1.) Please post also the error messages.
2.) Have you already tried to locate the error?
3.) Which compiler / version are you using?

---

