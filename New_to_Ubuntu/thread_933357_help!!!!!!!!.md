---
title: "?????? help!!!!!!!!"
date: 2008-09-29
forum: New to Ubuntu
---

### Post by rodneys392005 on 2008-09-29
im new on here to trying to get exe files to open and run but cant how do i get my downloads to open when done everything ive dl cant open getting really frustrated here love the os just dont know how to work it yet please if ya can help

---

### Post by Het Irv on 2008-09-29
Heh, yeah I imagine you would have a problem with .exe files.  .Exe's are built for a windows environment and therefore do not work in Linux.

You have a couple of choices, first and probably best, look for native Linux programs that do the same the programs you are trying to install now

Second you can WINE, which is a compatibility layer that allows you to run Windows apps in Linux, but it is far from perfect

Lastly, you can use a virtual Machine to run Windows inside of Linux, this works great for small apps, but games are a no-go.

---

### Post by Perfect Storm on 2008-09-29
.exe files are for Windows. You install stuff with synaptic Package Manager (System ---> Administration ---> Synaptic Package Manager) or with add/remove


What do you seek? We may come up with some alternatives.

---

### Post by SpenceMakesSense on 2008-09-29
lol well if you are that desperate to use .exe install wine
```
sudo apt-get install wine
```
But dont expect to be able to run EVERYTHING

---

### Post by rodneys392005 on 2008-09-29
oh ok well where would i find the safari for linix ubuntu and how do i get the file types i need for this?

---

### Post by Perfect Storm on 2008-09-29
Well, if the person don't know how to do general things, it woudn't be a good idea to let them start messing with wine which can be tedious even for experienced users.

---

### Post by Delvien on 2008-09-29
> **rodneys392005 said:**
> oh ok well where would i find the safari for linix ubuntu and how do i get the file types i need for this?

There is no Linux version of Safari, Firefox should do all you want, and is a lot more expandable than Safari is (if you are into this)

---

### Post by Kimm on 2008-09-29
> **rodneys392005 said:**
> oh ok well where would i find the safari for linix ubuntu and how do i get the file types i need for this?

You wont find Safari for Linux (there is no such thing..).
Stick to Firefox (its a better browser anyway), or check out Opera, Konqueror or Epiphany.

---

### Post by rodneys392005 on 2008-09-29
where do you get sudo or wine

---

### Post by Perfect Storm on 2008-09-29
There's also Epiphany browser if you're looking for lightweight browser. Or Opera.

---

### Post by Perfect Storm on 2008-09-29
> **rodneys392005 said:**
> where do you get sudo or wine

It's commands. The one that is shown will install wine, but you can find it in add/remove (Apllications tab).

The terminal to type commands; Applications tab ---> Accessories ---> terminal

---

### Post by rodneys392005 on 2008-09-29
cool thanks i like the firefox just thought id give the safari a try if i could what sites do you use for getting dls for this os that will let ya try new things i do need a file manager tho i cant get any type of file i dl to open what would ya suggest

---

### Post by wladicus on 2008-09-29
> **rodneys392005 said:**
> where do you get sudo or wine
**sudo**  is a Linux command that is entered from within a terminal window.  Wine is the program that permits the running of some Windows stuff.

---

### Post by SuperSonic4 on 2008-09-29
Nautilus is the file browser in GNOME. If you open any location it should open in Nautilus, I wouldn't put on a different browser.

Downloads come from the repositories most often (Add/Remove Programs, Synaptic or the terminal). [This thread]("http://ubuntuforums.org/showthread.php?t=766683") should help you get codecs et al installed. debs can be found at [http://getdeb.net](http://getdeb.net) (which are closest to .exe files) or developer's website itself

---

### Post by sydbat on 2008-09-29
All the programs you will need are in Synaptic Package Manager or Add/Remove...

Synaptic - System > Administration > Synaptic Package Manager

Add/Remove...  -Applications > Add/Remove...

---

### Post by jerome1232 on 2008-09-29
There is a ton of software included in what are called repositories for Ubuntu. If you goto Applications->Add/Remove... you will get a listing of the officially supported software for Ubuntu (there's alot).

For more advanced package management you can use synaptic, System->Administration->Synaptic Package Manager

sudo is an included program in Ubuntu used to access administrative features

apt-get is the cli way of installing software from the repos 

sudo apt-get install opera would be the command line way to install the program opera on your computer.

Using the repos is preferred because all apps installed this way get automatically updated by your system.



When looking around the internet for apps (try the repos first seriously I have only had to go outside of them twice for an app) look for Debian packages (.deb) If you went to opera's web site it will offer you a Debian install package.

---

### Post by rodneys392005 on 2008-09-29
thanks eveyone!

---

### Post by AgainstTheDarkArts on 2008-09-29
A lot of times I wonder "why do I run Linux, when windows does everything I want to do."

Then I try to imagine asking basic windows questions in a windows forum without getting a rude and/or obnoxious response, and I realize why Linux is right for me.

+5 to the whole forum, for (un)common decency and respect.

Note to the OP:  **sudo** is the way to run a single command from root, so that you can't accidentally leave your computer unlocked.  To balance security with usability, sudo stays on for a limited time (measured in minutes) so you don't have to type your password for every command. 

loosely translated:

apt-get install ...  <- this is the 'software installation' program

sudo apt-get install ... <- this temporarily 'unlocks' root so the program can be installed.

---

