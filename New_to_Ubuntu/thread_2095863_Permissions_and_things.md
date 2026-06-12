---
title: "Permissions and things"
date: 2012-12-18
forum: New to Ubuntu
---

### Post by gokiwi on 2012-12-18
Hi,

Absolute beginner to Linux and Ubuntu and wondering what the hell I have got myself into.

I am nearly (but not quite) 50 years old and have only ever used Windows products.

Trying to install an application called OpenNMS but need to edit files and add software etc but need to be able to login as root to get access to edit these files etc , but unlike Windows there is no ability to login as root and therefore you cannot do anything !

I have opened a command prompt thingy and entered su root and put in the password but this does nothing. I still cannot edit(?) anything.

Can someone help please before I either throw this damn machine out of the window or reformat it with Windows ?

Oh this is where I have got stuck, not even got out of the starting blocks !

To set up APT to talk to the OpenNMS repository, you'll need to create a file called "opennms.list" within the "/etc/apt/sources.list.d" directory, with the following contents: 
  # contents of /etc/apt/sources.list.d/opennms.list  deb [http://debian.opennms.org](http://debian.opennms.org) ***stable*** main  deb-src [http://debian.opennms.org](http://debian.opennms.org) ***stable*** main 

Scott

---

### Post by Lars Noodén on 2012-12-18
You can get a root shell with 'sudo -i'   However, be aware that it is easy break things in a very big way and that little mistakes can often become big mistakes when done as root.  Unfortunately, OpenNMS does not seem to be in Ubuntu's repositories, which would be the prefered way.  So you will have to install it by hand.

---

### Post by westie457 on 2012-12-18
Welcome to the Forum.

You do not need to log in as Root. That practice is frowned on in these Forums.

You do however need temporary Root privileges and for that preface the commands with sudo (except when running GUI apps use gksudo instead. Examples of these ```
sudo apt-get update
``` and ```
gksudo nautilus
```

Read this page [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) for more information.

I realise this will not install Opennms for you it might give you a clearer understanding of Root and sudo. Thus giving you a chance to install.

---

### Post by audiomick on 2012-12-18
> **gokiwi said:**
> I am nearly (but not quite) 50 years old and have only ever used Windows products.

So am I, but I got onto Linux about 6 years ago. Still learning... ;)
> 
Can someone help please before I either throw this damn machine out of the window or [COLOR="Red"]reformat it with Windows[/COLOR] ?
NO, NO, DON'T DO IT!!!:shock:

> 
Trying to install an application called OpenNMS

Are you following these instructions?
[http://www.opennms.org/wiki/Installation:Debian]("http://www.opennms.org/wiki/Installation:Debian")

If not, you should be, but I think you are.





> Oh this is where I have got stuck, not even got out of the starting blocks !

To set up APT to talk to the OpenNMS repository, you'll need to create a file called "opennms.list" within the "/etc/apt/sources.list.d" directory, with the following contents: 
  # contents of /etc/apt/sources.list.d/opennms.list  deb [http://debian.opennms.org](http://debian.opennms.org) ***stable*** main  deb-src [http://debian.opennms.org](http://debian.opennms.org) ***stable*** main 

There is a GUI way to do this (i.e. using graphical tools rather than the command line) in Ubuntu.

Open the software centre. In the "edit" menu, choose "package sources". You will be asked for your password. Go to the tab "other software" and click on "add". Put the url from the instruction above in the box. 

To do it from the command line.

You are wanting to create a file in a folder belonging to root, so you need to start the editor with root privileges. The syntax for creating a file with gedit is "gedit </path/to/filename>"
So you need to do
```
gksudo gedit /etc/apt/sources.list.d/opennms.list
```
which should open a new file in the editor that will be saved to the location you have specified when you opened it.

> 
 but need to edit files and add software etc but need to be able to login as root to get access to edit these files etc ,

You can't log in as root on Ubuntu. Linux does always have a root account, but it is disabled in Ubuntu. The mechanism that is used to carry out administrative tasks is sudo. If it is a command in the terminal that runs in the terminal, you put sudo in front of the command.
```
sudo <command>
```
You will be asked for your password, but wont see what you type when you enter it. Type the password and hit enter.

If the command invokes a graphical application, you should use gksudo to avoid a small chance of messing up some file permissions.
[http://www.psychocats.net/ubuntu/graphicalsudo]("http://www.psychocats.net/ubuntu/graphicalsudo")
That site is, incidentally, worth browsing. There is some good stuff there.

Anyway, we were on gksudo. You will have noticed it is in the command above to open gedit to deal with files owned by root. Gksudo invokes the password box, the same as when you want to install via the software centre or whenever else the system needs root privileges to do something.

Another useful one is
```
gksudo nautilus
```
to open an instance of the file manager as root. This allows you to use, for instance, graphical tools to change permissions on files that belong to root, or open a file belonging to root in the editor to be edited by clicking on it. 
Actually, you normally should not be changing permission on files that belong to root, but occasionally one gets created with the wrong permissions, and only root can save the world. Be careful with the file manager with root permissions. Don't invoke it unless you specifically need it, and close it a soon as you have finished. You can do a lot of damage to your system in there, as you also can by invoking the editor gedit with root privileges. There are lots of good reasons why a linux system is not normally used as root.

---

### Post by gokiwi on 2012-12-18
Thanks for the help and the welcome.....I have managed to get opennms installed and sort of running. I now have even more questions than answers !.

I think this is either going to be a very short affair or a very frustrating one ...time will tell.

Once again thanks to all =D>

---

### Post by snowpine on 2012-12-18
In the future you can simply say "hi, how do I do ___ in Ubuntu?" rather than all the drama. We are a helpful bunch here, and Ubuntu is very easy to use if you follow a few basic rules. ;)

---

### Post by Pjotr123 on 2012-12-18
> **gokiwi said:**
> I now have even more questions than answers !.

I think this is either going to be a very short affair or a very frustrating one ...time will tell.
Choose the operating system with which you feel most comfortable, of course.... No worries either way. :cool:

But maybe you'll feel better about your Linux and more confident, when you understand how installing applications takes place in Linux:
[https://sites.google.com/site/easylinuxtipsproject/applications](https://sites.google.com/site/easylinuxtipsproject/applications)

I'm the same age as you, by the way.... and I find Ubuntu to be almost boringly easy and maintenance free. The thing just works, as reliable as the Diesel engine of a truck. Provided that you treat her right: [https://sites.google.com/site/easylinuxtipsproject/fatalmistakes](https://sites.google.com/site/easylinuxtipsproject/fatalmistakes)

Anyway, happy trails, wherever they may lead...

---

### Post by gokiwi on 2012-12-18
Obviously my first post and a cry for help after spending nearly 6 hours trying to get this to work has caused offence.

So not the place for me after all.

Mods or whoever runs this forum please feel free to delete my account I wont be back !.


> **snowpine said:**
> In the future you can simply say "hi, how do I do ___ in Ubuntu?" ***_rather than all the drama._*** We are a helpful bunch here, and Ubuntu is very easy to use if you follow a few basic rules. ;)

---

### Post by snowpine on 2012-12-18
Oh dear, I am sorry if I offended you... my intention was the exact opposite: to give you **encouragement** that using Ubuntu can be a very calm, stable, reliable, and drama-free experience, with the help of these friendly forums. If you check my post history you'll see that I have welcomed and assisted many new users on these forums. [Here is a link]("http://www.catb.org/~esr/faqs/smart-questions.html") I found helpful when I was starting, to help me understand the Linux culture and use these forums effectively. I am glad that you have solved your problem and I apologize if I have inadvertently caused you offense. :)

(edit) I also feel compelled to say that I am just some random guy on the internet. I don't work for Ubuntu Corp. or contribute to its code. Even if you think *I* am a complete jerk, why should that change your opinion of Ubuntu? That's like giving up on a beloved sports team just because some random drunk guy at the game shouted something obnoxious. ;)

---

### Post by Zill on 2012-12-18
> **gokiwi said:**
> Obviously my first post and a cry for help after spending nearly 6 hours trying to get this to work has caused offence.

So not the place for me after all...
Firstly, don't worry about your age - there are many of us Linux users here quite a bit older than you. ;-)

I am sorry you experienced problems with software installation but you will always be able to find help on these forums.  All we ask is that posts are clear and concise, primarily containing a factual question, rather than "comment".  The forums have a very high level of traffic and so it helps experienced users to respond with help if posts are kept short as possible, while still containing the essential information.  Please also ensure your posts always have a clear and meaningful title relating to the specific problem.

The other advice I would give is that "[Linux is not Windows]("http://linux.oneandoneis2.org/LNW.htm")" and so you will have to expect to do things differently to the way things are done with Windows.  This takes some getting used to but, with time, you will come to appreciate the many great advantages of Linux.

If you do have any problems please feel free to post back.

---

### Post by iponeverything on 2012-12-18
look - no harm, no foul - 

OP goes back to then environment he's comfortable with, we go back to helping out where we can and everyone is happy. 

on a side note, I met the openNMS developers a while back outside the Motley Fool offices (when they were by the river) in Alexandria, Va. must have been 10 years ago.

Felt at the time that it was overly complex, but in hind sight - they made good design choices..

---

