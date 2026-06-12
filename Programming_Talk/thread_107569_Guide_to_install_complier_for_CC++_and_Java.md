---
title: "Guide to install complier for C/C++ and Java"
date: 2005-12-23
forum: Programming Talk
---

### Post by healychan on 2005-12-23
After a long time of searching and testing, I managed to install the JDK and gcc for programming practice. Here is the summary of my experience. I hope it can help you and save your time.

**[SIZE="3"]If you want to program with C/C++ please do the following:[/SIZE]**

[COLOR="Red"]sudo apt-get install build-essential[/COLOR]

this will install the header files, make and debugger for C/C++. You can now programming with C/C++:razz: 
(p.s. the command above was taken from [http://www.ubuntuforums.org/showthread.php?t=106574#4](http://www.ubuntuforums.org/showthread.php?t=106574#4) )


[SIZE="3"]**To those who want to install the Blackdown JDK 1.4.**[/SIZE]

[COLOR="Red"]1.[/COLOR] You need to enable multiverse and universe first. This link [http://help.ubuntu.com/starterguide/C/faqguide-all.html#addinguniverse](http://help.ubuntu.com/starterguide/C/faqguide-all.html#addinguniverse) will guide you to do so.
[COLOR="Red"]2.[/COLOR] Search for j2sdk1.4 and install that package.


[SIZE="3"]**To those who want to install the lastest Sun JDK 1.5 update 6.**[/SIZE]

[COLOR="Red"]1.[/COLOR] Goto [http://java.sun.com/j2se/1.5.0/download.jsp](http://java.sun.com/j2se/1.5.0/download.jsp).
[COLOR="Red"]2.[/COLOR] Select the "Download JDK 5.0 Update 6"
[COLOR="Red"]3.[/COLOR] Download the "Linux self_extracting file". Not the RPM one. (64 bit user please download the "Linux AMD64 self_extracting file".
[COLOR="Red"]4.[/COLOR] Move the bin file to the directory wherever you like.
[COLOR="Red"]5.[/COLOR] On the command line. type "./filename" where the filename is the bin file you downloaded. [COLOR="Red"]Make sure[/COLOR] you have the execute permission for this file.
[COLOR="Red"]6.[/COLOR] Add the of path to the $PATH. The path depends on where you put the bin file. For example, if you put the bin file in "/usr/lib/", then the whole path should be "/usr/lib/java/bin".


[SIZE="3"]**Install Sun JDK as a debian package**[/SIZE]
[COLOR="Red"]1.[/COLOR] Goto [http://java.sun.com/j2se/1.5.0/download.jsp](http://java.sun.com/j2se/1.5.0/download.jsp).
[COLOR="Red"]2.[/COLOR] Select the "Download JDK 5.0 Update 6"
[COLOR="Red"]3.[/COLOR] Download the "Linux self_extracting file". Not the RPM one. (64 bit user please download the "Linux AMD64 self_extracting file".
[COLOR="Red"]4.[/COLOR]make sure you install fakeroot package.
[COLOR="Red"]5.[/COLOR]chmod +x to the bin file you just download
[COLOR="Red"]6.[/COLOR]type "fakeroot make-jpkg {the bin file name}", this will create a debian package
[COLOR="Red"]7.[/COLOR]type "sudo dpkg -i {the deb file name}", this will install the debian package you created. You can now program with java:razz: 
[COLOR="Red"]8.[/COLOR]finally, move the deb file to /var/cache/apt/archives/ directory. This is optional.


[SIZE="3"]**Setup the PATH for java etc..**[/SIZE]
This is easy. Type
[COLOR="Red"]sudo update-alternatives --config java[/COLOR]
a list of options will be display, pick the java you want to use by putting a number.
EEEEEEEEEasy:p 

There are many ways to add the path to $PATH. You can either do it in ~/.bashrc or /etc/skel/.bashrc or /etc/bash.bashrc 
Please feel free to ask any question if you get confuse;) 

To check which java you are using, type "java -version". Check the version display to see if it is what you want. Set the PATH again if it is not the java you expected.



Also, if I made any mistake here or you know a better way to install, **PLEASE** reply and let us know. Thanks;)

More information here [http://java.sun.com/j2se/1.5.0/install-linux.html#self-extracting](http://java.sun.com/j2se/1.5.0/install-linux.html#self-extracting)
and here [http://www.docuverse.com/blog/donpark/EntryViewPage.aspx?guid=f171bafc-abce-4d2e-a18b-3aba4ad32c52](http://www.docuverse.com/blog/donpark/EntryViewPage.aspx?guid=f171bafc-abce-4d2e-a18b-3aba4ad32c52)

---

### Post by EnGee on 2005-12-23
Thanks for the Guide :)
I think there is a better way (and little bit longer) to install Java (and related IDEs) :
1.[http://www.docuverse.com/blog/donpark/EntryViewPage.aspx?guid=f171bafc-abce-4d2e-a18b-3aba4ad32c52](http://www.docuverse.com/blog/donpark/EntryViewPage.aspx?guid=f171bafc-abce-4d2e-a18b-3aba4ad32c52)
2.[http://blogs.sun.com/roller/page/coldrick?entry=java_development_on_ubuntu_part](http://blogs.sun.com/roller/page/coldrick?entry=java_development_on_ubuntu_part)

---

### Post by Revert on 2005-12-23
Can you walk me through how to set the path?  It's installed (think I used Automatix this time around), and I can compile, but I can't run it (get the NoClassDefFoundError each time).  I saw in another thread something concerning JAVA_HOME variable.  Does that need to be set by hand too?  If so, how do you do that?

Sorry, still pretty new to Linux. ;)

Edit: Error's taken care of; it was due to a lack of command line familiarity on my part.

---

### Post by EnGee on 2005-12-23
Revert
I consider myself new to linux also ;)
Anyway here what i did (I suppose you installed the Sun JDK 5 the right way):
1. Open the terminal and write sudo gedit
2. Browse and open bash.bashrc in /etc directory and add these lines in the end of the file :
export JAVA_HOME=/usr/lib/j2sdk1.5-sun/
export JDK_HOME=/usr/lib/j2sdk1.5-sun/

Some of the programs are searching for the second line! so it won't hurt to add it. Save the file (and I don't remember if you need to restart).
It should be another elegant way, but anyway it works for me.

I don't know if this is related to the error you have! What java -version tells you?

---

### Post by healychan on 2005-12-23
[QUOTE=Revert]Can you walk me through how to set the path?  It's installed (think I used Automatix this time around), and I can compile, but I can't run it (get the NoClassDefFoundError each time).  I saw in another thread something concerning JAVA_HOME variable.  Does that need to be set by hand too?  If so, how do you do that?

Sorry, still pretty new to Linux. ;)[/QUOTE]

Could you post the output of:
echo $PATH

---

### Post by healychan on 2006-01-04
I made some changes to the guide. I added the instruction about how 
to install java as a debian package.

This is a lot easier for the people who are not familiar with Linux administration 
since you can use Synatic Package Manager to maintain your package.

I also describe how to edit the PATH a bit.

Please reply if I made any mistake and I will fix it as soon as possible
Thx;)

---

### Post by coredump on 2006-01-04
I'd just like to point out (because I wasn't aware of it myself) that the C compiler (GCC) and all the 'build-essential' stuff is on the Ubuntu install CD-ROM.  This means that you don't need a network connection to install the compiler!  All you have to do is run Synaptic from the desktop menu and select the packages, with the CD-ROM ready in the drive.  Then, when you click on 'Accept', it reads the CD-ROM and installs the packages you've requested.

I'd made the assumption that the installer installs everything that's on the CD-ROM, and I'd have to use a broadband connection to download 'gcc'.  In fact, 'gcc' is right there on the CD-ROM, just not installed.

Hope that helps somebody.

---

### Post by migraineboy on 2006-01-07
[QUOTE=healychan]
[SIZE="3"]**To those who want to install the lastest Sun JDK 1.5 update 6.**[/SIZE]

[COLOR="Red"]1.[/COLOR] Goto [http://java.sun.com/j2se/1.5.0/download.jsp](http://java.sun.com/j2se/1.5.0/download.jsp).
[COLOR="Red"]2.[/COLOR] Select the "Download JDK 5.0 Update 6"
[COLOR="Red"]3.[/COLOR] Download the "Linux self_extracting file". Not the RPM one. (64 bit user please download the "Linux AMD64 self_extracting file".
[COLOR="Red"]4.[/COLOR] Move the bin file to the directory wherever you like.
[COLOR="Red"]5.[/COLOR] On the command line. type "./filename" where the filename is the bin file you downloaded. [COLOR="Red"]Make sure[/COLOR] you have the execute permission for this file.
[COLOR="Red"]6.[/COLOR] Add the of path to the $PATH. The path depends on where you put the bin file. For example, if you put the bin file in "/usr/lib/", then the whole path should be "/usr/lib/java/bin".


[SIZE="3"]**Setup the PATH for java etc..**[/SIZE]
This is easy. Type
[COLOR="Red"]sudo update-alternatives --config java[/COLOR]
a list of options will be display, pick the java you want to use by putting a number.
EEEEEEEEEasy:p 

There are many ways to add the path to $PATH. You can either do it in ~/.bashrc or /etc/skel/.bashrc or /etc/bash.bashrc 
Please feel free to ask any question if you get confuse;) 
[/QUOTE]

All right I made everything you told me to do, but, I'm sorry, I'm just a noob, I really don't know what means the step number six. I've made the step number five and after I agreed with the terms, aparently the java was installed. But I don't know how to do the final step to make it works...
Withou making the step number six I type sudo update-alternatives --config java and no option of java 1.5.0_06 show, only the 1.5.0_05 version appears. the bin file is in /home/arilson and in the terminal I just typed "./filename". Can you tell me exactly what I have to type to finish the step number six.
P.S: sorry for any errors in my english, I'm brazilian.

---

### Post by healychan on 2006-01-07
[QUOTE=migraineboy]All right I made everything you told me to do, but, I'm sorry, I'm just a noob, I really don't know what means the step number six. I've made the step number five and after I agreed with the terms, aparently the java was installed. But I don't know how to do the final step to make it works...
Withou making the step number six I type sudo update-alternatives --config java and no option of java 1.5.0_06 show, only the 1.5.0_05 version appears. the bin file is in /home/arilson and in the terminal I just typed "./filename". Can you tell me exactly what I have to type to finish the step number six.[/QUOTE]

I assume you install java within your home directory "/home/arilson".
If you type "ls" in there, you should see a directoy named "j2sdk1.5-sun".
If you can find "j2sdk1.5-sun", than do the following.

1. cd
2. gedit .bashrc
3. add "export PATH=/home/arilson/j2sdk1.5-sun/bin:$PATH"  to the end of the file
4. save file and restart the Terminal

Now type "echo $PATH"
If you can find "/home/arilson/j2sdk1.5-sun/bin" in the output, it is done:razz: 


> P.S: sorry for any errors in my english, I'm brazilian.

You don't have to say sorry, in fact, I am Chinese:razz: 

Good luck!!!!!

---

### Post by migraineboy on 2006-01-08
[QUOTE=healychan]I assume you install java within your home directory "/home/arilson".
If you type "ls" in there, you should see a directoy named "j2sdk1.5-sun".
If you can find "j2sdk1.5-sun", than do the following.

1. cd
2. gedit .bashrc
3. add "export PATH=/home/arilson/j2sdk1.5-sun/bin:$PATH"  to the end of the file
4. save file and restart the Terminal

Now type "echo $PATH"
If you can find "/home/arilson/j2sdk1.5-sun/bin" in the output, it is done:razz: [/QUOTE]

yeap, it completely worked!! Thanks a lot guy, you're the man!!


> You don't have to say sorry, in fact, I am Chinese:razz: 

Good luck!!!!! COOL!!!

P.S: any idea on making it work with firefox?

---

### Post by healychan on 2006-01-12
[QUOTE=migraineboy]P.S: any idea on making it work with firefox?[/QUOTE]
Sorry for the late reply, you may solve the problem already.
I couldn't remember what I did to install the plugin for firefox.
You can try to create some links in firefox plugin directory which point to the files in the jre directory.

---

