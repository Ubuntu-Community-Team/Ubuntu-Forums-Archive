---
title: "File I/O in C++"
date: 2008-01-18
forum: Programming Talk
---

### Post by roberto22085 on 2008-01-18
I am writing a program in C++ to keep track of certain information (for my sisters home business). Any way, one of the things I am keeping track of is contact information. Example:

First name, last name
address
city, state zip
phone number

here is how they are written to the file:

John Doe 123 Example Street. City State Zip 555-555-5555

What I need to do is read in the information back to the program. My problem is figuring out how to read in the address. I have been trying to use getline() but I can't get it to work.

here is what i have so far:

ifstream >> firstName >> lastName;
getline();
ifstream >> city >> state >> zip >> phone;

I know I need to read in the line up to a '.' (my delimiter) but I don't know how to do it with getline, or if that is even the correct way.

Help!!

Thanks in advance!

---

### Post by LaRoza on 2008-01-18
It would make sense to store this in a database. 

If C++ is not a hard requirement, I recommend Python and SQLite, if C++ is needed, I still recommend SQLite.

---

### Post by stevescripts on 2008-01-18
> **LaRoza said:**
> It would make sense to store this in a database. 

If C++ is not a hard requirement, I recommend Python and SQLite, if C++ is needed, I still recommend SQLite.

+1 re SQLite - whether you choose Tcl, Python,or *whatever* language

Steve

---

### Post by dwhitney67 on 2008-01-19
Using a database to store the client's information will make it easier should that information need to be modified or deleted in the future.

If you still want to continue with the flat-file, try delimiting each field, so that you do not have to worry about spaces.  You never know... maybe a client will have a first name of "Bobby Sue".

FirstName~LastName~Street Address~City~State~ZipCode~TelephoneNumber~

P.S.  I should add that it would be more efficient to read one entire line at a time, then parse it.  Disk I/O is costly in terms of computing time.

---

### Post by roberto22085 on 2008-01-19
Well I do actually know a little bit of Python, just basics. Should I install SQLite (server) or should I just use pysqlite? 

There is just one issue with writing my program in something other than C++, I already have 1700 lines of code, and I'd really like not to re-write the whole program! Can C++ also use SQLite??

Thanks!

---

### Post by slavik on 2008-01-19
If C++ is not a hard requirement, I would not recommend Python. Or any other programming/computer language for that matter

The problem that needs to be solved is to store addresses, not to write a program that does it.

Have you looked at OObase or Microsoft Access?

OObase has the added feature of being able to use a real database, to which it can connect over the network/internet.

---

### Post by dwhitney67 on 2008-01-19
> **roberto22085 said:**
> Well I do actually know a little bit of Python, just basics. Should I install SQLite (server) or should I just use pysqlite? 

There is just one issue with writing my program in something other than C++, I already have 1700 lines of code, and I'd really like not to re-write the whole program! Can C++ also use SQLite??

Thanks!

Below is a simple demonstration of what I mentioned earlier concerning delimiting each field:

[PHP]#include <fstream>
#include <iostream>
#include <sstream>

using namespace std;

int main()
{
  ifstream inFile( "./data" );

  if ( inFile )
  {
    string line;
    getline( inFile, line );

    while ( !inFile.eof() )
    {
      stringstream str( line );

      string firstName;
      string lastName;
      string streetAddr;
      string city;
      string state;
      string zip;
      string telephone;
      const char delimeter( '~' );

      getline( str, firstName,  delimeter );
      getline( str, lastName,   delimeter );
      getline( str, streetAddr, delimeter );
      getline( str, city,       delimeter );
      getline( str, state,      delimeter );
      getline( str, zip,        delimeter );
      getline( str, telephone,  delimeter );

      cout << "firstName  = " << firstName  << endl;
      cout << "lastName   = " << lastName   << endl;
      cout << "streetAddr = " << streetAddr << endl;
      cout << "city       = " << city       << endl;
      cout << "state      = " << state      << endl;
      cout << "zip        = " << zip        << endl;
      cout << "telephone  = " << telephone  << endl;
      cout << endl;

      getline( inFile, line );
    }
  }
  else
  {
    cerr << "Error, could not open file './data'" << endl;
  }

  return 0;
}[/PHP]

---

### Post by roberto22085 on 2008-01-19
Thanks dwhitney67!

I will try it out later, I don't have time right now.

I will post back later if it works or not.

I have also been in the process of learning SQLite, via [SQL Course.]("http://sqlcourse.com")

---

### Post by aks44 on 2008-01-19
> **roberto22085 said:**
> There is just one issue with writing my program in something other than C++, I already have 1700 lines of code, and I'd really like not to re-write the whole program! Can C++ also use SQLite??

SQLite is a C library, so you'll have no problem at all using it from C++.


Regarding your existing 1700 loc: this is quite a small amount of code, so if you decide to switch languages it will be straightforward to rewrite that. IMHO you'd better evaluate *now* what benefits you can get from C++, Python, or other languages, so that if you need to switch you won't loose much time.
The more you wait, the more you'll be tied to C++ due to your growing codebase, and the harder it will be to switch.

---

### Post by stevescripts on 2008-01-19
Folks, take a second to think back to when your first serious project reached 1700 or so LOC.  I'm sure it seems like a lot to roberto.  (that being said, I have trouble imagining this project reaching that many lines of code, especially sans file I/O)...

A little story for the original poster...

About 6 years ago, I did a single-purpose, random access flat--file database in C++ (the *last* non-trivial proggie I did in C++, FWIW).
It had to run on windows (where my users ran).  Although it had a CLI - I leveraged notepad/wordpad to save and print queries and reports.

After a couple of years of maintenance, and constantly having to go back to my source code, to add new queries, reports, etc.  I got kinda tired of messing around with the code.  So ... I wrote a little tcl script to export the db to a comma-delinited text file, hacked out a quickie SQLite db, and imported the file.  I have *NEVER* looked back.  Having SQL at hand to write queries as necessary, beats the H*** out of coding them in C++.

Again, just my $.02 - hope it helps.

Steve

---

### Post by LaRoza on 2008-01-19
> **stevescripts said:**
> 
Again, just my $.02 - hope it helps.


It should. Using SQLite (or other database solutions) is much better than storing information in text files. One ends up making a bad DB engine in the process, when simpler and easier solutions exist.

---

### Post by aks44 on 2008-01-19
> **stevescripts said:**
> Folks, take a second to think back to when your first serious project reached 1700 or so LOC.  I'm sure it seems like a lot to roberto.
I'm pretty sure too that 1700 loc looks like a lot of code to the OP. Which is why I mentioned that his project will probably continue to grow, and that *if* he wants to switch languages he'll be better off doing so soon, rather than waiting for his code to grow and thus having to migrate more code when/if he switches. :)

---

### Post by dwhitney67 on 2008-01-19
Maybe the OP only knows C++ (and C).  Maybe it's too much of a learning curve right now to learn another language.  Please understand that C++ has been around for a while, 1000's of programmers use it everyday.  Python is not the only language, and if it were that great, you would see it being used much more than C++.

The database suggestion is worthy.  With MySQL, and with the use of MySQL++, C++ can continued to be used.

</rant>

---

### Post by EXCiD3 on 2008-01-19
Better yet, give it a GUI and still use C++. Qt can do databases and its all super easy. You could quickly modify an example program to do this without taking much time at all.

---

