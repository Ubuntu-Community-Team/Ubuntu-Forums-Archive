---
title: "How can a perl programm open several other perl programs"
date: 2016-09-24
forum: Programming Talk
---

### Post by Roland_Msl on 2016-09-24
My main problem at changing from Windows to Linux had been my Perl / HTA programs, 
which I had to rewrite as client/server programs.

This is now finished, only one problem left.

My CMS has a start program, where all the sites, which can be edited are listed.
The CMS opens a browser window and communicates with XMLHttpRequest.

After clicking on a domain, there should be executed the perl program server.pl with some parameters.
Each site has assigned a port number for the communication from the perl script with the browser.

I start the whole system in gnome-terminal with

perl server.pl

This starts the overview with all sites for edit in the browser on port = 10500.

I tried several combinations to accomplish the task to open a new edit session with one of the sites
the last test was the following Perl line:

exec (	"gnome-terminal", "-e",	"$path::internet/cgi.pege.org/cgi-bin/server.pl task=WSC site=$site port=$port" );

This line 

opens a new terminal window like intended,
opens the editor in a new browser window for the clicked site like intended,
but terminates the program, what is not wanted.

It ends with the terminal window showing the prompt
and a new terminal window showing the messages of the edit this site session like intended.

What is wrong, that the Perl program ends, when this line is executed?

---

### Post by spjackson on 2016-09-24
The meaning of exec is to run the new program _instead of_ the current program; the current program ends with the call to exec. This is true for perl and all other environments that immediately spring to mind (bash, sh, C). You probably want to use system() or some other process control function.

---

### Post by Roland_Msl on 2016-09-24
Thanks,

I missunderstood the description of EXEC.

Only one more problem:

How can I prevent, that the terminal window opened with 

[COLOR=#000000]system (	"gnome-terminal", "-e",	"$path::internet/cgi.pege.org/cgi-bin/server.pl task=WSC site=$site port=$port" );

closes when the program ends?
[/COLOR]

---

### Post by spjackson on 2016-09-26
> **Roland_Msl said:**
> Thanks,

I missunderstood the description of EXEC.

Only one more problem:

How can I prevent, that the terminal window opened with 

[COLOR=#000000]system (    "gnome-terminal", "-e",    "$path::internet/cgi.pege.org/cgi-bin/server.pl task=WSC site=$site port=$port" );

closes when the program ends?
[/COLOR]

I think you probably want to use nohup e.g.
```

system("nohup gnome-terminal -e ls -laR / > /dev/null & ");

```

---

