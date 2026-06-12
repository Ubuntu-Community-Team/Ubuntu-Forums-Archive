---
title: "Code's that One Needs To Know."
date: 2008-09-13
forum: New to Ubuntu
---

### Post by icyest on 2008-09-13
With a plethora of a list of commands out there, what commands do you think every Linux user SHOULD know?
New people who attempt Linux for the first time often; to my observation, note that experienced people utilize the command prompt and assume you need expert "geek" knowledge simply to use a Linux; which quite possibly could be the most intimidating discouragement factor for anyone who only knows windows; and probably one of the reasons why Linux is associated into geek computer culture.

This is my second day diving into Linux with no prior experience, and I'd like to get my hands on Command Prompt.

Through you, the expert community's, public experience, what are the most common commands that you would advise for memorization?

I'm still starting out, so start basic. My aim is to also share your answers and help others get used to Linux. I'm afraid of doing something utterly harmful and irreversible, which may be common, but I trust this community.

---

### Post by crazypenguin2008 on 2008-09-13
in my opinion the terminal is still a great way to get things done within linux. over the past 4 years i have compiled a 2gb flash drive of commands and what they do. 

but im not at home and im not on my pc so i dont have that drive with me. soon as i get home sunday i can post my list of commands and what they do. 

the sudo commands are great to learn. 

and ill be damned if i can think of any off the top of my head

good luck and have a great time in linux!!

jas'

---

### Post by iaculallad on 2008-09-13
The best way for you to observe what this "expert community's" most commonly used terminal commands from day-to-day with Ubuntu is to login in the forum on your free time and try reading every posts and take note (as in scribe it in papers - as that was what I did when I was learning the terminal. You can't trust your memory) of the terminal commands being posted. Review and analyze the purpose of the command and watch out on dangerous commands. 
For more information about a terminal command, you can always consult your man page.

> man terminal_command

---

### Post by Greyed on 2008-09-13
man is the biggie.

```

man man

```

That command will explain why, seriously.  ;)

That and the tab key.  If you're going to operate on the CLI get used to bouncing on the tab key a lot.

---

### Post by Mister.Vash on 2008-09-13
You could start here:
[https://help.ubuntu.com/8.04/basic-commands/C/](https://help.ubuntu.com/8.04/basic-commands/C/)

Once you get comfortable with the basics, use the man program for commands you are not familiar with, such as
man ps
will provide information about the ps program

Search around google for bash tutorials, you get ones that tell you what you can do  - like the first hit that came up, [http://www.hypexr.org/bash_tutorial.php](http://www.hypexr.org/bash_tutorial.php) and ones that are more orientated towards writing scripts for bash.

A good way to pickup commands is to either have a goal in mind of what you want to do - as an example you want to rename a certain batch of files to all lower case in a folder, or just use command line programs instead of using the gui equivalent.  Use "sudo apt-get update" and "sudo apt-get upgrade" instead of System -> Administration -> Update Manager

The ones that you wind up using the most are the ones that you will memorize.  For ones that people suggest when you are trying to just do a specific thing that you don't run often, you'll want to be able to get you hands wrapped around what they are doing.  And for commands that you might only use once, or rarely, store them in a text file with a little comment of what they do so you can go back and reference it.

Do what you are comfortable with and what works for you.  I might need to change permissions on files on a regular basis because of running on a shared machine with multiple accounts, but you might never have to do that if you just have a single account on your machine, so pick up the general basics, and then start from there based on what you can do and what you want to do

---

### Post by t0p on 2008-09-13
Following iaculallad's advocacy of the **man** command, I'm going to suggest **apropos**.  Say you want to know how to do something concerning the mouse, but you don't know what the command is that you need. You type into the terminal:

```
apropos mouse
```

and ubuntu returns a list of mouse-related commands.

```
t0p@ubunty:~$ apropos mouse
kmousetool (1)       - KDE mouse manipulation tool
mdetect (1)          - mouse device autodetection tool
mouse (4)            - serial mouse interface
mousedrv (4)         - Mouse input driver
mousepad (1)         - simple text editor for Xfce
mousetweaks (1)      - Accessibility enhancements for the mouse
sol (6)              - a collection of card games which are easy to play wit...
vmmouse (4x)         - VMware Mouse input driver
vmmouse_detect (1)   - VMware mouse device autodetection tool
xeyes (1)            - a follow the mouse X demo
t0p@ubunty:~$ 


```

Very useful!

---

### Post by windozehater on 2008-09-13
I cant remember where i found these but they might help, they have given me some insight to start working with the term

[ATTACH]85073[/ATTACH]

---

### Post by skippuff54 on 2008-09-13
well you're probably gonna get a flood of items people think are important but let's start with this one concept: "sudo"

it stands for "super user do" and you'll often use this word in front of commands in order to get the highest credentialed access to your programs and files...many commands only accept a super user, or root user, to operate

then you also need to understand a couple of other things, like the file structure...anytime you're specifying a file, it's gonna be in the format /directory/subdirectory/file

commands sometimes use a similar structure, like /directory/subdirectory/command

and then sometimes you'll see that you can just use "sudo command" to make something work

furthermore, you'll notice that in those cases, you'll sometimes need to follow the command with a parameter to specify what exactly you want the command to do...for instance, the command "sudo shutdown -h now" means "super user shutdown halt now" which means "turn off the computer right now"

[LIST]
[*]"sudo apt-get install 'package'", with the certain name of a package, will go to the repositories, find a package (program) for you and automatically install it. often, after you perform this action you will need to configure the program, sometimes by GUI and sometimes by modifying the configuration file. for instance "sudo apt-get install samba" will go install samba, a package you'll need for networking with windows computers
[/LIST]

then i would also advise you to recognize that ubuntu, like all other forms of linux, are built on the unix shell, so many commands can be used on a variety of *nix systems

now as far as specific commands, you'll get to know those as you trudge through your configuration, which you'll find is gonna be particular to your needs...you will have to sort of mix and match configuration setups that you can find here on these forums, the wiki, ubuntuguide.org or the internet at large.

useful commands that come to mind are: 
[LIST]"grep" which means "get report" (followed by a certain device or program about which you need a report)
[/LIST]

[LIST]
[*]"cat" which will display the contents of a file without having to open it
[/LIST]

[LIST]
[*]"nano" is actually a text editor but you'll use it to open files that you modify (i.e. "sudo nano /etc/network/interfaces" will open your network interfaces file)
[/LIST]

[LIST]
[*]"modprobe" which helps you look for installed hardware (ie modprobe <module>)
[/LIST]

[LIST]
[*]"ifconfig" shows your active network interfaces and
[/LIST]

[LIST]
[*]"ifupdown" resets your network interfaces
[/LIST]

[LIST]
[*]"iwconfig" shows your active wireless interfaces.
[/LIST]

whew that's a mouthful, but you really need to get your mind around the file structure and permissions issues

---

### Post by skippuff54 on 2008-09-13
> **t0p said:**
> Following iaculallad's advocacy of the **man** command, I'm going to suggest **apropos**. 

Very useful!

no kiddin i just learned somethin, gracias

---

### Post by t0p on 2008-09-13
> **skippuff54 said:**
> 
[LIST]
[*]"modprobe" which helps you look for installed hardware (ie modprobe lspci)
[/LIST]


```
t0p@ubunty:~$ modprobe lspci
FATAL: Module lspci not found.
t0p@ubunty:~$
```

Yikes!

---

### Post by iaculallad on 2008-09-13
And learn to differentiate the use of **sudo** and **gksu/gksudo**. Do stick with sudo when running terminal commands that needs administrative privilege, and gksu/gksudo when running GUI applications that needs the admin privilege.

i.e:

```
sudo vi /etc/fstab
```

and

```
gksudo gedit /etc/fstab
```

Both commands above do the same function as opening the fstab file but opened using two different methods.

Same when using (k)Ubuntu:

**sudo** for terminal commands and **kdesu** for GUI applications.

---

### Post by skippuff54 on 2008-09-13
did i get that one wrong or somethin, i was tryin to list some off by memory

---

### Post by Oldsoldier2003 on 2008-09-13
> **t0p said:**
> ```
t0p@ubunty:~$ modprobe lspci
FATAL: Module lspci not found.
t0p@ubunty:~$
```

Yikes!

```
lspci
```

```
modprobe <some module_name>
```

---

### Post by skippuff54 on 2008-09-13
right thanks for cleanin that up

---

### Post by icyest on 2008-09-13
Thank you skippuff54 for giving the most insightful response. And yes, I notice that many of the commands offered by the community are of a huge variety of things I do not understand yet. Gratuitous as it may be, I hope these fall in the category of "basic" beginner's stuff. I should have probably included a mention in my origional post that says not to give extra necessary gratuitous code that most people may never use in their time with Ubuntu.

I apologize for mentioning Command Prompt in my initial post. I had forgotten that Linux refers to the code box as Terminal. I still have the taint of Microsoft.

Keep these replies coming, but please explain them well.  :]

I intend to use your advice to aid others too!

iaculallad, you mentioned gedit. I've seen that before when I experimented with Linux a few months ago. Can you explain this thing

---

### Post by skippuff54 on 2008-09-13
right no problem. take a look at the attached png file and link to basic commands posted earlier as well, those are good cheat-sheet type references.

another concept i thought i would mention is that of initialization. as your computer boots up, it will progress through several runlevels where it does things like look for your hardware, start services, etc. 

for example, it looks for sound and video cards, keyboard and mouse etc...then moves on to start up your network services, file sharing etc...then finally will start up your graphical user interface and that's when it goes from black and white to color login screen

so in diagnosing issues (that you are certain to have at some point), pay attention to what's being initialized and look for any error messages during these stages.

all of these items are initialized by what's called a boot script, which is an executable file that's run at boot time...that brings me to another couple of commands. BE CAREFUL with these, you might not wreck your system but you can cause yourself some headaches if used improperly...only use them if you know exactly how to do what you intend

[LIST]"chmod" changes the scope of modifications that can be performed on a file...you'll follow the command with numbers that determine whether a user can read, write and execute a file...for instance "chmod 777 file" will allow ANY USER to read, write and execute a file[/LIST]

[LIST]"chown" changes the ownership of a file. sometimes when you create a file, you want it to have root or superuser ownership, and you can use the command "chown root file" to make that change...likewise you can input any user to make it that user's file, ie "chown user file"[/LIST]

another couple that stood out to me on the references from earlier are [LIST]
[*]"cd" which changes the directory. for instance "cd /etc" will put you in the /etc directory
[*]"ls" lists the contents of the active directory.
[*]so in combination, you can do in the terminal "cd /etc" followed directly by "ls" to change to the /etc directory and list the contents
[/LIST]

now if you are working with any type of network, i would advise installing openssh, which gives you a secure shell terminal connection between your computers...then you can do all the handy terminal stuff from another machine

one last one i'll mention for now is "wget" which allows you to download a file from the command line. follow the command with the full URL of your file. you might need this if you are ever installing a package that isn't kept in the repositories...one that comes to mind is webmin, which is a web-based tool for configuring a number of server applications like apache, php and mysql

finally i have to agree with others that hitting roadblocks and performing searches is how you're really gonna get intimate with specific commands. just try to be as specific as possible in your search terms, posts and thread titles. google when you need to, and remember that it's very likely that others have run into similar issues before you.

---

### Post by lian1238 on 2008-09-13
**skippuff54** mentioned 'cd' which I use a lot. Say, you want to access a file from the current directory. Use the "." (dot) to inidicate 'this' directory, the one you're in. For example, if you want to use 'nano' to open a file called 'notes' on your desktop, you need to one of the following: ```
nano ~/Desktop/notes
```note that the '~' is your HOME directory which is equivalent to /home/yourname/
By default, the terminal opens in your home, so you can do```
cd Desktop
nano ./notes
```Note that you can leave out the './' altogether, but it's useful when you want to run a file in 'this' directory, but you also want to use the auto-completion (tab). Using tab without the './' will also give you bash commands.
Another useful thing is going up one directory.
```
cd ../
```This is bring you to the parent directory (same as Alt+UP in nautilus - the default file browser in ubuntu)
```
cd ../../
```for going up two levels.

That's my part on cd. Happy commanding!

---

### Post by Greyed on 2008-09-13
> **t0p said:**
> Following iaculallad's advocacy of the **man** command, I'm going to suggest **apropos**.

Never understood this one.  man -k is shorter and easier to remember (unless you're French, I guess).  ;)

---

### Post by Vivaldi Gloria on 2008-09-13
There are a number of commands that give general info about your hardware:

```
lshw
hwinfo
dmidecode
```

If any of these are not installed then search & install them using synaptic.

Preferably use these (and the ones at the end of this post) with sudo:

```
sudo lshw
```

etc. (Sudo gives administrative rights.)

These spit out so much info that it may be better to save the output into a text file:

```
sudo lshw > info1.txt
sudo hwinfo  > info2.txt
sudo dmidecode  > info3.txt
```

Start by using the short versions

```
sudo lshw -short
sudo hwinfo --short
```

They have flags to restrict the output to certain hardware. For example

```
sudo lshw -class system
sudo dmidecode -t system -t baseboard

```

give motherboard info. To learn more about these flags see their man pages:

```
man lshw
man dmidecode
man hwinfo

```

Some other commands:

```
lspci [COLOR="DimGray"](Lists PCI devices including Audio, VGA, Ethernet etc.)[/COLOR]
aplay -l [COLOR="DimGray"](sound info)[/COLOR]
uname -a [COLOR="DimGray"](kernel info)[/COLOR]
lsb_release -a [COLOR="DimGray"](which version of ubuntu)[/COLOR]
lsusb [COLOR="DimGray"](list USB devices)[/COLOR]
ls /dev/disk/* -lah [COLOR="DimGray"](disk mount and uuid info)[/COLOR]
fdisk -l [COLOR="DimGray"](disk info)[/COLOR]
df -h [COLOR="DimGray"](disk usage info)[/COLOR]
free -m [COLOR="DimGray"](memory info)[/COLOR]
cat /proc/swaps [COLOR="DimGray"](swap file/partition info)[/COLOR]
smartctl [COLOR="DimGray"](check health status of a disk)[/COLOR]
cat /proc/cpuinfo [COLOR="DimGray"](cpuinfo)[/COLOR]

```

and the list goes on and on. Some of these need sudo in front of them.

---

### Post by Too Late on 2008-09-13
One of my favorite commands (wasn't mentioned yet):
```
less
```
For example, "less ~/file.txt" or "dmesg | less" (where dmesg can be any command that posts much output). Press q to quit. See "man less" or "less --help" for more.

---

### Post by icyest on 2008-09-15
So Vivaldi, these are windows equivalent to dxdiag?:

lshw
hwinfo
dmidecode


Also, just for curiosity, is it possibly to uninstall Synaptic? I mean, it's a program after all, or is it just a fundamental piece of Ubuntu that cannot be destroyed? I know Win XP had a bunch of things built in that you can't get rid of.

---

### Post by Vivaldi Gloria on 2008-09-15
> **icyest said:**
> So Vivaldi, these are windows equivalent to dxdiag?:


I don't know what dxdiag is so I have no idea. :-)

> Also, just for curiosity, is it possibly to uninstall Synaptic?

In theory you can uninstall synaptic and use apt-get (aptitude, dpkg etc.) in the command line to install programs. I don't know what happens in practice because I've never tried it.

---

