---
title: "Java GUI to MySQL database Q"
date: 2007-04-14
forum: Programming Talk
---

### Post by derby007 on 2007-04-14
General Q: 
I have my database (relational) designed, i have my GUI designed, and now i'm setting up a way to get the data to/from the database. I currently have a Connect class, an Insert class, & a Query class. The Insert class sends the data down with Prepared statements. Note: i dont have classes for my Tables, ie. objects mapping to Tables. 

I am also looking at StoredProcedures......if I go this route will my design change??

So: I'm looking for direction or advise as to the (dare i say it) BEST way or more straight-foreward way of getting data to/from GUI's to DB's. 
Is the way i'm doin it....acceptable ! (on a small scale).

NOTE: this is a standalone GUI and not multi-user or web-based....yet.

---

### Post by phossal on 2007-04-14
Code that works is good code. Depending on how large your application is, you may not need a class dedicated to every process. In other words, you don't need a class to do updates, a class to do selects, and a class to do inserts. If your application is small enough, just use a single class that handles your data movement to and from the application. If you're determined, create a separate class for the connection (you'll probably build other applications that use the same DB), and one to wrap JDBC calls (you'll need class that does a bunch of little generic tasks like handling null values, formatting dates, etc. Such tasks get monotonous.)

---

### Post by derby007 on 2007-04-14
Yeah I have a few generic ones, my latest one is a Date class that returns current Date & a determined future Date. My windows/frames map to the Database fairly well so I might not need Table Objects...!! 
Have you used Stored Procedures, any tips/guidelines.....

---

### Post by phossal on 2007-04-14
Yeah, I've used a few stored procedures. lol I've even done it for sport: [Java Object Serialization.]("http://ubuntuforums.org/showthread.php?t=372931") I don't have any tips, really. Any working code is good code. You can always go back and improve it later - or not.

Regarding dates, try to create a class that will mimic the getter methods of a ResultSet. For example, getDate(), etc. You want to be able to wrap your result set and call simple methods, without having to worry about null values or other errors every time. Just like creating a separate class for your connection, a ResultSet 'helper' class is something you'll move from application to application.

---

### Post by derby007 on 2007-04-14
Actually here is my 1st rev of getDate(), no doubt I can improve on it, it was interesting as i just used the java.sql.Date, there surley is more classes based around Date out there...

/*
 * getDate.java
 *
 *
 */

package dataBase;

import java.sql.Date;
import java.lang.Integer;



public class getDate {
    
    private Date d = null;
    private String [] months = {"January","February", "March", "April", "May",
                "June","July","August","September","October","November","December"};
    private int currentYear = 0;
    private int endYear = 0;
    private int currentMonth = 0;
    private int endMonth = 0;
    
    public getDate() {
        d = new Date(System.currentTimeMillis());
    }
    
    public String getCurrentDate(){           
        currentYear = (d.getYear()) +1900 ;
        currentMonth = d.getMonth() +1;         // Start of NEXT Month
        
        //System.out.println( "StartMonth : "+months[currentMonth] );
        //System.out.println( "StartYear :"+currentYear );        
                
        return ("1st of "+months[currentMonth]+" "+currentYear);
    }
    
    
    public String getEndDate( int in ){        
        int monthTest = currentMonth;       
        int yearTest = currentYear;
        int year = 11;       
        int check = ( year-monthTest );     
                
        if( check >= in ){                      // If 'value in' doesn't go beyond the Current Year
            monthTest += in;
            endMonth = monthTest-1;             // 'End Month' is the end of the last active month
            endYear = currentYear;
        }else{            
            monthTest += in;                    // Add 'value in' to 'test month'
            do{
                monthTest -= year;              // Keep taking 11 from 'value in' 
                if( monthTest==1 ){             // Must Rollback to December if month is January
                    monthTest=11;
                    endMonth = monthTest;
                    endYear = yearTest;
                }else{
                    yearTest++;                 // Go to the following year 
                    endMonth = monthTest-2;     // 'End Month' is the end of the last active month
                    endYear = yearTest;
                }
                
            }while( monthTest > year );         // Check if 'test month' is > 11
            
        }         
        //System.out.println( "EndMonthFinal : "+endMonth );
        //System.out.println( "EndYearFinal :"+endYear);
        
        return ("Last day of "+months[endMonth]+" "+endYear);        
    }
    
}

---

### Post by phossal on 2007-04-14
Oh, wow. That's a lot of hard work. I like the array of month names. You might consider using Calendars while you're working with dates. As you progress, you'll undoubtedly work with them, and learning them might help you here.

[EDIT] Let me add a bit more emphasis: You *certainly* want to investigate Calendar objects.

---

### Post by phossal on 2007-04-14
Here is an example for you:

```
import java.util.Calendar;
import java.util.Date;

public class Calendar_Object {
	public static void main(String args[]) {
		
		Date now = new Date();
		Calendar now_calendar = Calendar.getInstance();
		
		now_calendar.setTime(now);		//Use the date object to set the time.
		int year                  = now_calendar.get(Calendar.YEAR);
		int day_of_month    = now_calendar.get(Calendar.DAY_OF_MONTH);
		int day_of_week     = now_calendar.get(Calendar.DAY_OF_WEEK);
		int month               = now_calendar.get(Calendar.MONTH)+1;
		
		System.out.println("Date: "+month+"/"+day_of_month+"/"+year);
		
		/* Technically you don't need to create the Date object. You can just use Calendar.getInstance() which 
		 * creates a calendar initialized to the current date. But I want you to see how you insert a date, which 
		 * you'll be working with from your Result Set.
		 */
	}
}
```

---

### Post by derby007 on 2007-04-14
YEAH, i heard about the Calendar class after i used the deprecated functions in java.sql.Date class.....

---

