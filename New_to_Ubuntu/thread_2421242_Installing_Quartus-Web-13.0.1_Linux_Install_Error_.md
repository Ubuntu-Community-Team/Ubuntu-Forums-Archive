---
title: "Installing Quartus-Web-13.0.1 Linux Install Error Ubuntu Desktop 18.04 LTS"
date: 2019-06-18
forum: New to Ubuntu
---

### Post by shahan27 on 2019-06-18
[COLOR=#242729][FONT=Arial]Hello everyone I am new to Linux and having issues to install this software [Quartus II Web Edition]("http://fpgasoftware.intel.com/13.0sp1/?edition=web&platform=linux&download_manager=dlm3")(13.0sp1 version) on Ubuntu Desktop 18.04 LTS.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]What I have done already was download the package of Quartus and extracted the files to my desktop. The following files were extracted: an setup.sh file and a folder called components which contains .qdz and .run files. Now I tried multiple ways to run this setup.sh file such as:

 Also keep in mind I gave permission to the sh file and checked off the box "Allow executing file as program"[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]
First Attempt: 
cd Desktop 
./setup.sh 
(nothing happened)[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]
Second Attempt:
 sudo passwd 
root sudo su 
cd Desktop 
chmod 755 setup.sh 
./setup.sh 
(Nothing happens just goes back to the regular command line on terminal)[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]
Third Attempt:
 I tried to double click the setup.sh file because I seen post where it should give an option that says "Run in terminal" but what happens for me is it opens the sh file in a text edit and there is no option to open with terminal and run.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial][URL="https://i.stack.imgur.com/VMiWL.png"]

Photo of what happens when I run ./setup.sh and what the contents of the sh file has and the permission it has[/URL]

[/FONT][/COLOR]

---

