---
title: "Writing a program that communicates with internet"
date: 2007-05-11
forum: Programming Talk
---

### Post by ghandi69_ on 2007-05-11
Hey guys, I am in the middle of working on a program that is going to analyze statistics for some of my fantasy baseball teams.

I am currently using c++, and at the moment I am copy/pasting the information from the internet into a text file and then adding it all up from there. Using c++, would there be a way to create an interface where it would go to the correct url address, and grab the information and write it to a text file all by itself?

If c++ is not the best way of doing this, please let me know what you guys feel the best path to take.  I know you could write a webpage in PHP that can do this, but I'd like this to be a program that stays on your computer and only has to access the internet once to get the information.

---

### Post by lloyd_b on 2007-05-11
Take a look here: [libcurl documentation]("http://curl.haxx.se/libcurl/")

There are bindings for many different languages (including C++).

To use it in your program, you'll need to install the packages "libcurl3" (if it's not already installed), and "libcurl3-dev" (for the development headers).

Lloyd B.

---

### Post by hartz on 2007-05-11
Can you please give a more clear explanation of what the program is meant to do?

---

### Post by ghandi69_ on 2007-05-11
> **hartz3 said:**
> Can you please give a more clear explanation of what the program is meant to do?

Ok, well, I'm writing two of them, the one I described above about statistics, and now another that will simulate a 'fantasy baseball draft'.  I will try to give you an explanation about the 'draft' program because it is the simpler of the two.

When the program starts, it will ask you how many teams you plan to have in your fantasy baseball league, you can enter how many, and then it will ask you to name each team.  The program will then create a blank text file for every team.  Then, I was hoping to add a feature where you can "retrieve player rankings", where it will go to one of the fantasy baseball websites, and get a complete list of major league ball players, their positions, and where they are "ranked" according to the site.

Once this is done, the program will randomly determine a draft order, and then it will be the first teams turn to select a draft pick.

The screen will print out a list of all the players currently available(reading from the text file), allow the user to narrow his search by position.  When the user selects a player, it will remove that player from the master list and place him on the team's text file.  Continue until you choose to quit.

The part I have no idea how to being with is being able to go online and retrieve this player lists.

Again guys, thanks for the help.

---

### Post by cwaldbieser on 2007-05-12
> **ghandi69_ said:**
> Ok, well, I'm writing two of them, the one I described above about statistics, and now another that will simulate a 'fantasy baseball draft'.  I will try to give you an explanation about the 'draft' program because it is the simpler of the two.

When the program starts, it will ask you how many teams you plan to have in your fantasy baseball league, you can enter how many, and then it will ask you to name each team.  The program will then create a blank text file for every team.  Then, I was hoping to add a feature where you can "retrieve player rankings", where it will go to one of the fantasy baseball websites, and get a complete list of major league ball players, their positions, and where they are "ranked" according to the site.

Once this is done, the program will randomly determine a draft order, and then it will be the first teams turn to select a draft pick.

The screen will print out a list of all the players currently available(reading from the text file), allow the user to narrow his search by position.  When the user selects a player, it will remove that player from the master list and place him on the team's text file.  Continue until you choose to quit.

The part I have no idea how to being with is being able to go online and retrieve this player lists.

Again guys, thanks for the help.

The libcurl suggestion above is good if you really want to keep everything in C++.  However, there are a bunch of shell tools that can accomplish retrieving files from the Internet very easily including curl, wget, etc.

---

### Post by hartz on 2007-05-12
Hi there ghandi69_

I have a feeling a language like Perl or Java would be better suited to this problem.  It is not that it cannot be done in C or C++, it is just that the nature of the problem doesn't justify the level of granularity that C or C++ gives you.

You could write the whole program as a shell script.  wget is the command to use to retrieve web-based info (URLs) from the net into a text file (or other file, depending on what it is you are retrieving).

But both java and perl has got "modules" with functions specifically made to retrieve information from the net.

Of course there are C / C++ libraries that will do this too.  So it is just my opinion.

Have a look around cpan for perl examples on how to get info/data from the net.  I found this example: [http://www.cpan.org/authors/id/E/EL/ELIJAH/bget-1.2](http://www.cpan.org/authors/id/E/EL/ELIJAH/bget-1.2)

---

