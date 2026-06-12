---
title: "Beginner Programming Challenge #2"
date: 2009-03-28
forum: Programming Talk
---

### Post by run1206 on 2009-03-28
ok, Bodsda asked if I could come up with the next challenge, so here's challenge #2!

**[size=3]Challenge:[/size]** Make a program (using any language desired) that will calculate the average miles per hour for a road trip.

The input will come from a file, the output can be either another file or standard terminal output. Your parameters will be...

1. Number of miles at the start of the trip.
2. Number of miles at the end of the trip.
3. Number of seconds of the total trip.

You could do more than three parameters but these three are the main parameters to use (start1, end1, time1, start2, end2, time2, etc...)

after the program receives the inputs, calculate the miles per hour. If you use more than one set of parameters, calculate the "cumulative" miles per hour. Figure out how to convert the seconds to hours for proper calculation.

**[size=3]Extra Credit:[/size]** put the time in standard time format (11:30:00, 15:42:15, 23:59:59, etc...)  and calculate timing of hours and minutes from there.

Try to make your implementation as clean and as clear as possible, readable by beginners.  Any experts doing the coding, please help out any beginners having trouble with their code.

Should be fairly simple; i've done it in C++ but i'm curious how some other programs might do the procedure. Just remember to use File Input/Output when inputting the parameters. Good Luck!! :)

~run1206

---

### Post by elCabron on 2009-03-28
C#
```

using System;
using System.IO;

class MilesPerHour
{
    public static void Main(string[] args)
    {
        int totalMiles = 0, totalTrips = 0, totalSeconds = 0;
        int tripStart  = 0, tripEnd    = 0, tripSeconds  = 0;
        
        if ((args.Length != 1) || (File.Exists(args[0]) == false))
        {
            Console.WriteLine("Error: expecting valid filename as argument.");
            return;
        }

        try
        {
        
            Console.WriteLine("\n Trip     Start       End     Miles   Seconds       Mph");        
            string[] lines = File.ReadAllLines(args[0]);
            
            foreach(string line in lines)
            {              
                string[] tripParams = line.Split(' ');
                Int32.TryParse(tripParams[0], out tripStart);
                Int32.TryParse(tripParams[1], out tripEnd);
                Int32.TryParse(tripParams[2], out tripSeconds);                        
            
                int    tripMiles    = (tripEnd - tripStart);
                double milesPerHour = ((double)tripMiles) * (3600.0 / tripSeconds);
                Console.WriteLine("{0,5}{1,10}{2,10}{3,10}{4,10}{5,10:##}", 
                                   (totalTrips + 1), tripStart, tripEnd, tripMiles, tripSeconds, milesPerHour);
            
                totalMiles   += tripMiles;
                totalSeconds += tripSeconds;
                totalTrips++;
            }
            
            Console.WriteLine(new String('-', 55));
            Console.WriteLine("Number of trips: " + totalTrips);
            Console.WriteLine("Total distance (miles): " + totalMiles);
            Console.WriteLine("Total time (seconds): " + totalSeconds);
            Console.WriteLine("Average speed (mph): {0:##}", ((double)totalMiles) * (3600.0 / totalSeconds));
        }
        catch
        {
            Console.WriteLine("\n\nError parsing file!");
            Console.WriteLine("Expected file format:");
            Console.WriteLine("start1 end1 time1");
            Console.WriteLine("start2 end2 time2");
            Console.WriteLine("...");   
        }                
    }
}  
```

---

### Post by bruce2000 on 2009-03-28
challenge.py
```

#Read a file
in_file = open("challenge_data","r")
startMiles =int( in_file.readline())
endMiles=int(in_file.readline())
timeSec=int(in_file.readline())
in_file.close()

#calculate speed in mph
mph=(endMiles-startMiles) / (timeSec/3600)
print "Your speed for the journey was:",mph,"mph."

```

challenge_data
```

10
60
3600

```



No frills no error checking...

I've only started learning python recently, and this is the 1st program of my own that I've written.. very basic I know but I'm pleased with it hehe.

---

### Post by cardinals_fan on 2009-03-28
EDIT: Assume the input file (.traveltimes) is formatted like this:
```
0
200
15000
200
500
22000
500
750
17000
```
The average MPH for the whole trip (50) is given by this Perl script:```
#!/usr/bin/perl
use strict;
use warnings;

my $name = "/home/jesse/.traveltimes";
my @first;
my @second;
my @third;

open( my $R, '<', $name ) or die "couldn't open $name \n";

while ( my $line = <$R> ) {
		unshift(@first, $line);
	}

my $mph = ($first[1]-$first[8])/(($first[0]+$first[3]+$first[6])/3600);
print $mph;
```

---

### Post by Le-Froid on 2009-03-28
C++, not exactly sure if I did it right

mph.txt:
```

1
15
1200

```

mph.cpp
```

#include <iostream>
#include <fstream>
#include <cstdlib>

using namespace std;

int main(int argc,char* argv[])
{
	if ( argc != 2 ) // If there is no file specified
	{
		cout << "Usage: " << argv[0] << " FILE" << endl;
	}
	else
	{
		ifstream mph_file ( argv[1] ); // try to open the file
		if ( !mph_file.is_open() )
		{
			cout << "Error: Could not open file\n";
		}
		else
		{
			char temp[100];
			while(!mph_file.getline(temp, 100).eof())
			{
				//many variables
				char start[10];
				char time[40];
				char minutes[40];
				float hours;
				float val;
				float start_val;
				
				mph_file.getline(start, 10); // get miles
				mph_file.getline(time, 40); // get seconds
				
				// convert distance and timing into floats
				val = atoi(time);
				start_val = atoi(start);
				
				// turn seconds into an hour
				hours = val / 3600;
				
				// say the mph
				cout << start_val / hours << " miles per hour\n";
			}
		}
	}
}

```

---

### Post by FireFoxer on 2009-03-30
Run1206,

What do you mean by miles at the start of the trip and miles at the end of the trip?  Doesn't it make more sense to simply give the miles traveled and the time in seconds?

I will code this up tomorrow sometime.

---

### Post by run1206 on 2009-03-30
> **FireFoxer said:**
> Run1206,

What do you mean by miles at the start of the trip and miles at the end of the trip?  Doesn't it make more sense to simply give the miles traveled and the time in seconds?

I will code this up tomorrow sometime.

some trips might not start at 0 miles.  maybe 1200 miles or some other non-zero number.  sorry for not clarifying that before :oops:

---

### Post by Bodsda on 2009-03-30
Heres my solution in python

[php]
#! /usr/bin/env python

# Beginner programming challenge #2
# By Bodsda

import os               # This module will be used to clear the terminal of previous commands etc and also for file checking.

def clear():            # Defines a function called clear() that performs the line below
    os.system('clear')  # This will cause the terminal running the program to run its 'clear' command


def main():
    clear()
    good = 0            # Will be used to exit a loop

    print """Welcome to Bodsda's solution to 
    run1206's Beginner Programming Challenge #2\n"""    # The triple quote is used to span the print statement across multiple lines
                                                        # The '\n' is a newline escape character, meaning when it is encountered a new line is printed
    while good == 0:                                    # Do things in loop until good does not equal 0
        
        file_path = raw_input("Please enter the path to the infile: ")  # Get the file path 
        if '~/' in file_path:                                           # Check if they are using ~/ to denote /home/username
            file_path = os.path.expanduser(file_path)                   # expand ~/ to /home/<username>
        elif file_path == "exit":                                       # Exit if input is 'exit'
                exit()

        try:                                                            # Try to open file, if success exit loop
            infile = open(file_path)
            good = 1
        except IOError:                                                 # If the file does not exist, catch the error and print an error message
            print "Error: File does not exist, check your spelling"

    lines = infile.readlines()                                          # Read the file
    count = 0                                                           # Will be used to iterate over the list index
    while count != len(lines):                                          # In the loop, remove trailing newline characters
        lines[count] = lines[count].rstrip("\n")
        count += 1
    start, end, time = int(lines[0]), int(lines[1]), int(lines[2])      # Set 3 variables from the infile
    print start, end
    miles = end - start
    hours_remainder = time % (60 * 60)                                  # Claculations
    hours = time / (60 * 60)
    minutes = hours_remainder / 60
    seconds = hours_remainder % 60
    print "Your journey totalled %i miles and took %i:%i:%i" % (miles, hours, minutes, seconds)         # Print the time


main()
[/php]

I know it looks a bit messy, but thats due to the comments, looks fine in fullscreen vim

Thanks,

Bodsda

---

### Post by Bodsda on 2009-04-05
@ run1206: Any ideas when this is gonna get judged?

---

### Post by run1206 on 2009-04-05
> **Bodsda said:**
> @ run1206: Any ideas when this is gonna get judged?

i'll do the judging on Monday and announce the winner on Tuesday.

---

### Post by Bodsda on 2009-04-05
Hopefully you'll get some more entries by then :)

---

### Post by kpatz on 2009-04-05
> **FireFoxer said:**
> What do you mean by miles at the start of the trip and miles at the end of the trip?  Doesn't it make more sense to simply give the miles traveled and the time in seconds?

I will code this up tomorrow sometime.The idea is that you would enter your car's odometer reading at the beginning and end of the trip, and have the program calculate the number of miles traveled.

---

### Post by fiddler616 on 2009-04-05
> **Bodsda said:**
> Heres my solution in python

[php]
#! /usr/bin/env python
#Trim
    good = 0            # Will be used to exit a loop

#Trim
    while good == 0:
#Trim
[/php]

I know it looks a bit messy, but thats due to the comments, looks fine in fullscreen vim

Thanks,

Bodsda
It's a very small point, but with an eye to readability and (however marginal) performance, maybe
[PHP]
good == False
...
while not good:[/PHP]
instead?

---

### Post by GF_Sobriquet on 2009-04-05
Here is my submission in very C-esque C++, it assumes a properly formatted input file if it can open it. That is, some multiple of 3 lines where each set of 3 lines is:
```
odometer at start
odometer at end
travel time in seconds
```
[PHP]#include <iostream>
#include <fstream>
#include <string>
#include <cstdlib>

using namespace std;

int main(int argc, char *argv[]) {
	
    if(argc != 2){
		cout << "You must provide an input file!" << endl;
		cout << "Try it like this:" << endl;
		cout << argv[0] << " <filename>" << endl;
		return 1;
	}
   
	ifstream inFile;
	inFile.open( argv[1] );
	if( !inFile.is_open() ) {
		cout << "Error: input file problem, make sure it exists and all that" << endl;
		return 1;
	}else {
	    string line;
		int startMiles, endMiles, travelTime;
		float mph;
		float mphTotal = 0;
		int tripNumber = 0;
		/* read in the file 3 lines at a time */
		while( !getline(inFile,line).eof() ) {

			startMiles = atoi( line.c_str() );
			
			getline(inFile,line);
			endMiles = atoi( line.c_str() );

			getline(inFile,line);
			travelTime = atoi( line.c_str() );

			tripNumber++;

			/* calculate the mph */
			mph = (float)(endMiles-startMiles) / (float)travelTime * 3600;
			mphTotal += mph;
			cout << "Trip " << tripNumber << " mph: " << mph << endl;
		}
		mphTotal = mphTotal / tripNumber;
		cout << "Average mph for all trips: " << mphTotal << endl;
		inFile.close();
	}
	return 0;
}
[/PHP]

Edit: Here is another attempt after reading some ifstream documentation. This reduces the required libraries and makes things more C++ like:
[PHP]
#include <iostream>
#include <fstream>

using namespace std;

int main(int argc, char *argv[]) {
	
    if(argc != 2){
		cout << "You must provide an input file!" << endl;
		cout << "Try it like this:" << endl;
		cout << argv[0] << " <filename>" << endl;
		return 1;
	}
   
	ifstream inFile;
	inFile.open( argv[1] );
	if( !inFile.is_open() ) {
		cout << "Error: input file problem" << endl;
		return 1;
	}else {
	    int line;
		int startMiles, endMiles, travelTime;
		float mph;
		float mphTotal = 0;
		int tripNumber = 0;
		/* read in the file 3 lines at a time */
		while( inFile >> line) {

            startMiles = line;

			inFile >> line;
			endMiles = line;

			inFile >> line;
			travelTime = line;

			tripNumber++;

			/* calculate the mph */
			mph = (float)(endMiles-startMiles) / (float)travelTime * 3600;
			mphTotal += mph;
			cout << "Trip " << tripNumber << " mph: " << mph << endl;
		}
		mphTotal = mphTotal / tripNumber;
		cout << "Average mph for all trips: " << mphTotal << endl;
		inFile.close();
	}
	return 0;
}
[/PHP]

---

### Post by OutOfReach on 2009-04-05
Practicing my structured programming in C...
It takes the file as an argument so:
```

./thisProgram data.txt

```
Would do.
[PHP]
#include <stdio.h>
#include <stdlib.h>

struct Node
{
    int error;
    int mStart;
    int mEnd;
    int secTotal;
};

// Prototypes
int CalculateMPH(struct Node info);
struct Node ReadInputFile(FILE *inputFile);

int main(int argc, char *argv[])
{
    if (argc == 1) {
        printf("Not enough arguments!\n");
        return 1;
    }

    FILE *inputFile;
    inputFile = fopen(argv[argc-1], "r");
    if (inputFile == NULL)
    {
        printf("fopen(%s) returned null, exiting...\n", argv[argc-1]);
        return 1;
    }


    struct Node MPH_Info;
    int MPH;
    do
    {
        MPH_Info = ReadInputFile(inputFile);
        if (MPH_Info.error == 1) {
            break;
        }
        MPH = CalculateMPH(MPH_Info);
        printf("Miles oper hour calculated: %i\n", MPH);
    }
    while (MPH_Info.error != 1);

    fclose(inputFile);
    return 0;
}

struct Node ReadInputFile(FILE *inputFile)
{
    struct Node tmp;
    if (fscanf(inputFile, "%i\n%i\n%i", &tmp.mStart, &tmp.mEnd, &tmp.secTotal) == EOF)
    {
        tmp.error = 1;
    }
    else
        tmp.error = 0;
    return tmp;
}

int CalculateMPH(struct Node info)
{
    int hrs = info.secTotal / 3600;
    int MPH = (info.mEnd - info.mStart) / hrs;
    return MPH;
}
[/PHP]

---

### Post by conehead77 on 2009-04-06
Some Haskell code using the Reader Monad / Monad Transformer:
[PHP]
import IO (readFile)
import Control.Monad.Reader (ask, runReaderT)
import Control.Monad.Trans (lift)

test :: IO ()
test = do
    content <- readFile "input"
    do initState <- ask 
       lift . putStrLn $ show $ process initState
       `runReaderT` content 
    return ()

calculateTriplet :: [Integer] -> Integer
calculateTriplet (start:end:seconds:_) = (end - start) * 3600 `div` seconds

process :: String -> [Integer]
process s = map calculateTriplet $ map (map read) $ map words $ lines s
[/PHP]

input:
```

10 60 3600
14 50 3870
11 63 3560

```

output:
```
[50,33,52]
```

---

### Post by gtr32 on 2009-04-06
C# using XML and datasets. This isn't an attempt to write the shortest possible code, obviously. The add trip function is just to get a correct file started as my coffee break is over and I need to get back to work. :)


```

using System;
using System.Collections.Generic;
using System.Text;
using System.Data;
using System.IO;

namespace trip
{
    class Program
    {
        // for demo purpose only, this needs to be implemented to
        // accept user input
        static void AddTrip(DataTable _trips)
        {
            int n = _trips.Rows.Count;
            DataRow _row = _trips.Rows.Add();
            _row["Start"] = n * 100;
            _row["End"] = (n + 1) * 100;
            _row["StartTime"] = DateTime.Now.AddHours(n);
            _row["EndTime"] = DateTime.Now.AddHours(n + 1);
        }
        
        static void Print(DataTable _trips)
        {
            long _lTotalDistance = 0;
            double _dTotalSeconds = 0;
            foreach (DataRow _row in _trips.Rows)
            {
                long _lDistance = (long)_row["End"] - (long)_row["Start"];
                TimeSpan _Span = (DateTime)_row["EndTime"] - (DateTime)_row["StartTime"];
                double _dAvSpeed = _lDistance / _Span.TotalSeconds * 3600;
                Console.WriteLine("**********************************************");
                Console.WriteLine("Distance\t:\t{0}km", _lDistance);
                Console.WriteLine("Time\t\t:\t{0}", _Span);
                Console.WriteLine("Averg. speed\t:\t{0:0.00} km/h", _dAvSpeed);
                Console.WriteLine("Start\t\t:\t{0}", _row["Start"]);
                Console.WriteLine("End\t\t:\t{0}", _row["End"]);
                Console.WriteLine("StartTime\t:\t{0}", _row["StartTime"]);
                Console.WriteLine("EndTime\t\t:\t{0}", _row["EndTime"]);
                Console.WriteLine("**********************************************");
                _lTotalDistance += _lDistance;
                _dTotalSeconds += _Span.TotalSeconds;
            }
            double dTotalAverageSpeed = _lTotalDistance / _dTotalSeconds * 3600;
            Console.WriteLine("**********************************************");
            Console.WriteLine("Total trips\t\t:\t{0}", _trips.Rows.Count);
            Console.WriteLine("Total Distance\t\t:\t{0}km", _lTotalDistance);
            Console.WriteLine("Total Time\t\t:\t{0}", new TimeSpan(0, 0, (int)_dTotalSeconds));
            Console.WriteLine("Total Averg. speed\t:\t{0:0.00} km/h", dTotalAverageSpeed);
            Console.WriteLine("**********************************************");

        }

        static void Main(string[] args)
        {
            if (args.Length < 2)
            {
                Console.WriteLine("Usage:\ntrip [OPTION] [FILE]\nTo add new trip use option -a\nTo print use option -p");
                return;
            }

            DataSet _data = new DataSet();
            DataTable _trips = _data.Tables.Add("Trips");
            _trips.Columns.Add("Start", typeof(long));
            _trips.Columns.Add("End", typeof(long));
            _trips.Columns.Add("StartTime", typeof(DateTime));
            _trips.Columns.Add("EndTime", typeof(DateTime));

            switch (args[0])
            {
                case "-a":
                    string resp;
                    do 
                    {
                        AddTrip(_trips);
                        Console.WriteLine("Add another? (yes/NO)");
                        resp = Console.ReadLine();
                    } while (resp.ToUpper() == "YES" || resp.ToUpper() == "Y");
                    try { _data.WriteXml(args[1]); }
                    catch (Exception ex) { Console.WriteLine(ex.Message); }
                    break;
                case "-p":
                    try { _data.ReadXml(args[1]); Print(_trips);}
                    catch (Exception ex) { Console.WriteLine(ex.Message); }
                    break;
                default:
                    Console.WriteLine("Usage:\ntrip [OPTION] [FILE]\nTo add new trip use option -a\nTo print use option -p");
                    break;
            }

        }
    }
}


```

---

### Post by Bodsda on 2009-04-07
> **fiddler616 said:**
> It's a very small point, but with an eye to readability and (however marginal) performance, maybe
[PHP]
good == False
...
while not good:[/PHP]
instead?

Cool, thanks, just found out then you can also use 'while not good' if good = 0, no need to convert to False it seems,

I could also have used 

While True and then just used break to exit the loop upon a condition

---

### Post by fiddler616 on 2009-04-07
> **Bodsda said:**
> Cool, thanks, just found out then you can also use 'while not good' if good = 0, no need to convert to False it seems,

I could also have used 

While True and then just used break to exit the loop upon a condition
This being Python, you're not supposed to worry about stuff like this, but having good be False makes it a boolean value, not an integer, and booleans take up less memory (but we're talking bits here)...I guess it's just good practice to use the simplest thing that gets the job done effectively.

---

### Post by run1206 on 2009-04-24
sorry i haven't been available for a while.  just landed a software engineering job in Princeton last Friday :D
i'll let Bodsa do the judging on this one as well.  i tested all the entries thus far and they worked for me. 
personally i like the C# entry gtr32 gave, but others were very concise and used many programming techniques.  hopefully more people hand in some more languages and codes in the future.

---

### Post by Bodsda on 2009-04-25
Hi, I have been asked to judge this challenge as run1206 currently does not have much time due to his/her new job (congrats) so I have looked over the entries and while they were all good, however I have to choose one winner, so without further ado, the winner is...

*Drum roll please*


=========================


Le-Froid


=========================

!!***Congratulations***!!

His clear code and useful comments make this C++ program a dream come true for any newbie programmer wishing to learn from some good examples. (Meaning I learned something from your code, so cheers :))

For everyone else that entered, well done, all the entries were good and again it was nice to see that not all the entries were in python. 

I now hand over to Le-Froid and request that he comes up with the next challenge. Just make a thread titled "Beginner programming challenge #3" 

Thanks to everyone who entered and I look forward to seeing you all in the next challenge,

Have a good day, Thanks,

Bodsda

---

### Post by run1206 on 2009-04-25
> **Bodsda said:**
> Hi, I have been asked to judge this challenge as run1206 currently does not have much time due to his/her new job (congrats) so I have looked over the entries and while they were all good, however I have to choose one winner, so without further ado, the winner is...

*Drum roll please*


=========================


Le-Froid


=========================

!!***Congratulations***!!

His clear code and useful comments make this C++ program a dream come true for any newbie programmer wishing to learn from some good examples. (Meaning I learned something from your code, so cheers :))

For everyone else that entered, well done, all the entries were good and again it was nice to see that not all the entries were in python. 

I now hand over to Le-Froid and request that he comes up with the next challenge. Just make a thread titled "Beginner programming challenge #3" 

Thanks to everyone who entered and I look forward to seeing you all in the next challenge,

Have a good day, Thanks,

Bodsda
HIS new job (i'm male :lol: )

congrats Le-Froid on winning!! :D :D :D

---

### Post by Le-Froid on 2009-04-25
Thank you, thank you :)

I always like doing these kind of challenges, its gonna be fun coming up with one on my own :)
I'll think of something to do in a day or two.

---

### Post by Bodsda on 2009-04-26
Congratulations again. I look forward to seeing the challenge :)

---

### Post by hakermania on 2010-03-15
Although this is closed, could I post my own prog here (and my own question....?)
Here it is:
```
#!/bin/sh
#hakermania for ubuntuforums.org
echo "Did you started from 0 miles? y or n"
read yn
if [ "$yn" = "y" ]; then
clear;
echo "So I am using 0 as your starting point"; sleep 1; clear
startmile=0
else
echo "From which mile did you started?"
read startmile
fi
echo "How many miles did you did?"
read endmile
echo "How many seconds did you trip lasted?"
read seconds

echo "scale=2;  3600*($endmile - $startmile)/$seconds " | bc > /home/$USER/Desktop/a
mph=`cat /home/$USER/Desktop/a`
rm /home/$USER/Desktop/a
if [ "$mph" -lt 0 ]; then
echo "Your speed was $mph mph ??? :S "
else
echo "Your speed was $mph mph"
fi
```
Well..Here is the output..Why does it says illegal number and illegal number????
```
How many miles did you did?
1
How many seconds did you trip lasted?
3600
[: 23: Illegal number: 1.00
Your speed was 1.00 mph

```
???

---

