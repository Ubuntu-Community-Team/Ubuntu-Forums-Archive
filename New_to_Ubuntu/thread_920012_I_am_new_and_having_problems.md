---
title: "I am new and having problems"
date: 2008-09-14
forum: New to Ubuntu
---

### Post by EdwardCullen on 2008-09-14
I currently converted from Windows XP OS to Ubuntu, and my Linksys Wireless USB Network Adapter does not work because it was made for Windows. Therefore what should I do, also remember I am a total noob, I just got Ubuntu 1 hour ago, so I have no clue. I tried reading other things about this but was confused, I know there is a way to do this, but how?

Thanks,

EdwardCullen

PS this was the topic I read, but I did not understand: [http://ubuntuforums.org/showthread.php?t=553822](http://ubuntuforums.org/showthread.php?t=553822)
Also I am on my computer with Vista which works, but Vista is horrid.

---

### Post by tuxxy on 2008-09-14
Heres a good [networking guide]("https://help.ubuntu.com/8.04/internet/C/index.html") 

ALso if you dont understand something, post which part you are having difficulty in understanding

---

### Post by EdwardCullen on 2008-09-14
I am having problems to fiqure out how to get the Linksys Wireless g USB Network adapter to work connect to internet.
I don't understand all of it pretty much :(

---

### Post by k33bz on 2008-09-14
> **EdwardCullen said:**
> I currently converted from Windows XP OS to Ubuntu, and my Linksys Wireless USB Network Adapter does not work because it was made for Windows. Therefore what should I do, also remember I am a total noob, I just got Ubuntu 1 hour ago, so I have no clue. I tried reading other things about this but was confused, I know there is a way to do this, but how?

Thanks,

EdwardCullen

PS this was the topic I read, but I did not understand: [http://ubuntuforums.org/showthread.php?t=553822](http://ubuntuforums.org/showthread.php?t=553822)
Also I am on my computer with Vista which works, but Vista is horrid.

actually, Linksys work very well with Linux, better with Linux than with windows. m(just my opinion)

---

### Post by crazypenguin2008 on 2008-09-14
i have the same exact linksys usb adapter on my second desktop and it conected right out of the box......same thing with my belkin usb wireless g usb adaptefr....

---

### Post by EdwardCullen on 2008-09-14
> **k33bz said:**
> actually, Linksys work very well with Linux, better with Linux than with windows. m(just my opinion)

I never said that, I just can not get it to work.

---

### Post by crazypenguin2008 on 2008-09-14
> **EdwardCullen said:**
> I currently converted from Windows XP OS to Ubuntu, and my Linksys Wireless USB Network Adapter does not work because it was made for Windows. Therefore what should I do, also remember I am a total noob, I just got Ubuntu 1 hour ago, so I have no clue. I tried reading other things about this but was confused, I know there is a way to do this, but how?

Thanks,

EdwardCullen

PS this was the topic I read, but I did not understand: [http://ubuntuforums.org/showthread.php?t=553822](http://ubuntuforums.org/showthread.php?t=553822)
Also I am on my computer with Vista which works, but Vista is horrid.

first line you state it was made for windows...wrong the linksys usb adapter is a universal wireless usb internet adapter. 

do you have wireless enabled??

---

### Post by k33bz on 2008-09-14
> **EdwardCullen said:**
> my Linksys Wireless USB Network Adapter does not work because it was made for Windows. 

????

It works better with linux than it does with windows!
they are not made for windows, they are made for networking any computer type network

---

### Post by crazypenguin2008 on 2008-09-14
did you enable wireless on the machine??

---

### Post by EdwardCullen on 2008-09-14
Yes I did

---

### Post by EdwardCullen on 2008-09-14
Also I need it for the Setup and it is a excutable file, could that be the problem?

---

### Post by crazypenguin2008 on 2008-09-14
did type in your network in the connection manager??

---

### Post by EdwardCullen on 2008-09-14
Where is the connection manger?

---

### Post by crazypenguin2008 on 2008-09-14
right click the siginal meter on the top bar on the right side. looks like a cell phone signial bar

---

### Post by EdwardCullen on 2008-09-14
I seen edit wireless networks, is that it?

---

### Post by crazypenguin2008 on 2008-09-14
yes thats it,and it will say edit wireless network and connect to other network

---

### Post by gunksta on 2008-09-14
To all of those who responded telling the OP how great the hardware works under linux, I feel obligated to remind you that this is not a good way to convince someone to use this as a resource.

To the OP,
Let's start with the basics. I'd like to see if you have an IP address while using Linux. Clearly your network is working since it works under Windows. I'm going to walk you through doing something on the command line. It's not strictly necessary, but it will give us a lot of information to help you diagnose your issue.

Go to Applications -> Accessories -> Terminal

This will start gnome-terminal. Alternatively, you can hit Alt-F2 and type in gnome-terminal.

Once you have gnome-terminal running, type this into the command line.

```
ifconfig
```

This should create a whole bunch of text. Note: This command won't alter anything on your computer, but it does help us know what's going on. Cut and paste the results here so we can see it.

---

### Post by crazypenguin2008 on 2008-09-14
i was just stating the facts that i have had zereo problmes getting mine to connect. and i do have wireless usb devices on 4 of my 5 pcs....

---

### Post by EdwardCullen on 2008-09-14
I went into Edit Wireless Network and I see a white empty box. to right is propertys.
I typed the name of my wireless network in and I go down into bssids, but It will not let me type anything in...

What should I do? Did I miss something somewhere?

---

### Post by EdwardCullen on 2008-09-14
> **gunksta said:**
> To all of those who responded telling the OP how great the hardware works under linux, I feel obligated to remind you that this is not a good way to convince someone to use this as a resource.

To the OP,
Let's start with the basics. I'd like to see if you have an IP address while using Linux. Clearly your network is working since it works under Windows. I'm going to walk you through doing something on the command line. It's not strictly necessary, but it will give us a lot of information to help you diagnose your issue.

Go to Applications -> Accessories -> Terminal

This will start gnome-terminal. Alternatively, you can hit Alt-F2 and type in gnome-terminal.

Once you have gnome-terminal running, type this into the command line.

```
ifconfig
```

This should create a whole bunch of text. Note: This command won't alter anything on your computer, but it does help us know what's going on. Cut and paste the results here so we can see it.
It has no internet so I can not cut it and paste it in anyway.

---

### Post by crazypenguin2008 on 2008-09-14
go in to change wireless network and type in your network and hit connect


is the router a wireless "g" i made the mistake and bought a wireless n adapter by accident once and it wouldnyt connect to my wireless g router

---

### Post by mdsmedia on 2008-09-14
> **crazypenguin2008 said:**
> i was just stating the facts that i have had zereo problmes getting mine to connect. and i do have wireless usb devices on 4 of my 5 pcs....I agree that it actually provides confidence that the hardware actually works with Linux, and as some have said....it WASN'T made for Windows, and it appears, to some, that it works better in Linux than in Windows, so it's NOT an issue of the hardware not working well with Linux.

---

### Post by EdwardCullen on 2008-09-14
Where is Change Wireless networks? Do you mean edit wireless networks?

If so, then I don't see connect.

---

### Post by starcannon on 2008-09-14
Check to see if it need proprietary drivers, 

{System>Administration>Hardware Drivers}

Enable the devices listed in there, is your linksys adapter showing up there? If not then we'll try something else.

---

### Post by EdwardCullen on 2008-09-14
> **crazypenguin2008 said:**
> go in to change wireless network and type in your network and hit connect


is the router a wireless "g" i made the mistake and bought a wireless n adapter by accident once and it wouldnyt connect to my wireless g router

It is wirless g

---

### Post by mdsmedia on 2008-09-14
> **crazypenguin2008 said:**
> go in to change wireless network and type in your network and hit connect


is the router a wireless "g" i made the mistake and bought a wireless n adapter by accident once and it wouldnyt connect to my wireless g routerWould that be similar in Windows or just in Linux? If it works in Windows, shouldn't it also work in Linux?

---

### Post by Slug71 on 2008-09-14
Have you enabled Wireless Permissions in System-Admin-Users and Groups?
Are the lights on, on your Wireless adaptor?

---

### Post by EdwardCullen on 2008-09-14
> **starcannon said:**
> Check to see if it need proprietary drivers, 

{System>Administration>Hardware Drivers}

Enable the devices listed in there, is your linksys adapter showing up there? If not then we'll try something else.

It is not listed there.....
Nothing is listed there

---

### Post by EdwardCullen on 2008-09-14
> **Slug71 said:**
> Have you enabled Wireless Permissions in System-Admin-Users and Groups?
Are the lights on, on your Wireless adaptor?

No I have not....How do I do that?
The lights are off and it is plugged up.

---

### Post by starcannon on 2008-09-14
{Applications>Accessories>Terminal}
```
sudo lshw -C network
```

copy paste the output of that command here.

---

### Post by EdwardCullen on 2008-09-14
Umm, The problem is, I am not connected to the internet. I am on a different computer than the computer I have Ubuntu on. I can not copy and paste the out put.

---

### Post by EdwardCullen on 2008-09-14
Also is it bad that the setup is Exe?

---

### Post by jakupl on 2008-09-14
well -  can you find a way of getting it and ifconfig here? maybe with a usb pen or similar?

---

### Post by jakupl on 2008-09-14
> **EdwardCullen said:**
> Also is it bad that the setup is Exe?

ubuntu can not read exe files.
exe are windows executional files.

---

### Post by EdwardCullen on 2008-09-14
My brother has the USb pin :(

---

### Post by EdwardCullen on 2008-09-14
> **jakupl said:**
> ubuntu can not read exe files.
exe are windows executional files.

Well how to make it non exe cause that is only way for setup?

---

### Post by starcannon on 2008-09-14
NM finished writing this post after it got stale. No pen drive, then that leaves the cat5 (network cable option)

ah gotcha, no place to plug it in to a network cable? if no, then is there a usb stick at your disposal? 

for usb stick

```
sudo lshw > ~/Desktop/Hardware.txt
```then drag and drop the new Hardware.txt file from your desktop to the thumdrive, and bring it over to your online computer that way.

GL

---

### Post by EdwardCullen on 2008-09-14
There is no USB stick at my diposial, I have no way to get it for you to see.

---

### Post by chriswyatt on 2008-09-14
Try left-clicking the wireless icon on the top-right, that'll show you a list of wireless networks, click on the one you want and type in either the WEP key or the WPA key, I actually found this less painful than Windows, and you don't have to enter it twice either (that's a stupid idea :lolflag:).  Sorry if I am misunderstanding things here or haven't looked through the thread properly.

---

### Post by Ptero-4 on 2008-09-14
> **chriswyatt said:**
> Try left-clicking the wireless icon on the top-right, that'll show you a list of wireless networks, click on the one you want and type in either the WEP key or the WPA key, I actually found this less painful than Windows, and you don't have to enter it twice either (that's a stupid idea :lolflag:).  Sorry if I am misunderstanding things here or haven't looked through the thread properly.

The problem is that the OP´s USB wifi dongle isn´t even getting detected.
To the OP. Can you find a floppy (assuming both of your PC´s have floppy drives) and pass the docs to the online PC? Also you might want to post your lsusb as well.

---

### Post by gunksta on 2008-09-14
> **EdwardCullen said:**
> It has no internet so I can not cut it and paste it in anyway.


If you go to the command line, as I explained in my previous post, and type in the command "ifconfig"; I promise the computer will respond. This command will print out the current network configuration, it does not require an internet connection to work.

The first step to diagnosing the problem is to see if the computer has an appropriately named network device. ifconfig is an easy way to do this. It will also show us if you have an IP address. Having an IP address is related but different from having the internet.

---

### Post by gunksta on 2008-09-14
> **EdwardCullen said:**
> Also is it bad that the setup is Exe?


You definitely don't need the setup file from Windows. It's useless on Linux.

Here's what we can do. On the Linux box, type in ifconfig. My computer spits back something that looks like this:

eth0      Link encap:Ethernet  HWaddr 00:0d:56:7d:f9:aa  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 

eth1      Link encap:Ethernet  HWaddr 00:04:23:6d:7f:67  
          inet addr:10.10.10.138  Bcast:10.10.10.255  Mask:255.255.255.0
          inet6 addr: fe80::204:23ff:fe6d:7f67/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:22114 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17228 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:24543200 (23.4 MB)  TX bytes:2295615 (2.1 MB)
          Interrupt:5 Base address:0xe000 Memory:fafef000-fafeffff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1466 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1466 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:73300 (71.5 KB)  TX bytes:73300 (71.5 KB)


There are three "paragraphs" to this response. You will probably also have 3. Give us the first line of all three (just type it in, we definitely don't need the one that starts with "lo").

Another alternative, is to plug the Linux box into the network with a network cable. Most WAPs have the option on the back if you happen to have any cables around. I'm sure the wired internet connection will be able to set itself up.

---

### Post by barx on 2008-09-14
Hi New guy, let me explain since the begining.

This problem has been resolved in this post:

[http://ubuntuforums.org/showthread.php?t=418925]("http://ubuntuforums.org/showthread.php?t=418925")

But If you are new of course you'll not understand it all.

First, look Aplications - Accesories - Terminal(in Spanish) or Console.

Second. You will see a new window maybe white background and black letters, and you will see "your user name"@"the name you putted to your computer":~$.
For Example you user name is "mijo" and the name of the computer is "tito", then in the console you will see this:
```
mijo@tito:~$
```
if you don't see simbols like these then is not a console :lolflag:

Third. When you see it it's time to pass to this step, you can cuztomize or decorate the console or terminal as you wish, like many things in ubuntu navigator and desktop, but you need internet first, so.

Type in the console:

```
mijo@tito:~$ sudo gedit /etc/modprobe.d/blacklist file
```

**sudo**, is a comand that give you permisions to the computer to do somethig to it, it's like when you say Please to somebody to ask for an unusual or personal thing(Sounds weird, but our computer with linux get personality :lolflag:).

**gedit** is a text editor, there's kate, mousepad and many you can use abiword, but you need it one of those[some of them must be installed], but when you're new and everythig gedit is by default

**/etc/modprobe.d/** is a folder of root[root is the name of the personanality of the computer that you got to be inside with sudo].

**blacklist file**, many of the times this texts or scripts or documents doesn't exists and you're creating in that time that's why are in blank,on the other hand; if has some letter and words means that it was created before.

Fourth. Okay the last large explanation was to make you know the meaning of each word, but I recomend you to do only what are specified instructions, because when you sudo a thing bad, you can hurt your computer, so, read and write.

when you type the line in the third step you now must hit enter, then it will apear a thing like this:

```
[sudo] password for mijo:
``` Remember thet mijo@tito:~$ is an example

you shall not see anything, but type you password and hit enter, but if you do it wrong you will see the next thing in terminal or console:

```
Sorry, try again.
[sudo] password for mijo:
```

I can't tell if the console will give you infinite oportunities, the most of the times I typed wrong my  password were 3 times, so I can't tell you if it's infinite, I have never tried.

Fifth. then you did the 3rd and 4rd steps correct it will appear[finally] a blank document or with words, so it doesn't matter, you will add the next list.

```
blacklist bcm43xx

blacklist rt2500

blacklist rt2561

blacklist rt25xx

blacklist rt2570

blacklist r8187

blacklist r818x

blacklist NET2280

blacklist ISL3886

blacklist islsm

blacklist p54u

blacklist islsm_usb
```

then, you must save and close.

Sixth. You now must to reboot you computer, it's what it says the post, sometimes you only need to restart X, but in this case are drivers, next time when the troubles could be less important hit **crtl** **alt**  **backspace**, and will return to the login seseion, but this time restart, so if you're in a cyber cafe, print this, but not leave already.

Seventh. Prepare an usb drive or memory to save this package:

[http://packages.ubuntu.com/feisty/net/ndisgtk/donwload]("http://packages.ubuntu.com/feisty/net/ndisgtk/donwload")

save this package to the memory. This program is in the ubuntu repositories, but if you don't have internet you can't donwload from your computer :lolflag:, so that's why the sacred task of that traveler device.

Eighth. run the package from your computer, yes It's a Deb, double-clicking the package will open a little window that appearsu to install the program, clic to install and will appear a graphical sudo, this time you'll see what you type in dots, yes dots, hit enter or accept and in some minutes the program wil be installed. 

Ninenth. Go to System[it's at the top next to places], Administration, Network and try to find your network. In case of not, go to Aplications, Internet, ndiswrapper or type in terminal or consile:

```
mijo@tito:~$ ndiswrapper -l
```

Hit enter and this will indicate if you have enabled the network. 

Tenth.I hope works for you or make you understand better the instructions, for a newbie it's confusing at first time, but then all that short and complex language will be easier to you with practice.
 
Believe me, it's better have problems of difficulties, because that's the way to learn and show you better how works linux.

for more details now visit this post:

[http://ubuntuforums.org/showthread.php?t=418925]("http://ubuntuforums.org/showthread.php?t=418925")

Sincerly Yours, Barz [that's sounds so gay :lolflag:]

---

### Post by barx on 2008-09-14
> **gunksta said:**
> If you go to the command line, as I explained in my previous post, and type in the command "ifconfig"; I promise the computer will respond. This command will print out the current network configuration, it does not require an internet connection to work.

The first step to diagnosing the problem is to see if the computer has an appropriately named network device. ifconfig is an easy way to do this. It will also show us if you have an IP address. Having an IP address is related but different from having the internet.
to copy and past text in terminal or console press **ctrl**  **shift**(the fat upper arrow)  **"v" to paste, "c" to copy and "x" to cut**.

you can only cut the tex t that you're writting in terminal, but it's not complicated, only you have to add ashift between the ctrl and the letter of your choise

---

### Post by tech.dummy on 2008-09-14
I have currently installed Ubuntu in my laptop (sharing with XP). Is there a way to make the applications shared between the XP and Ubuntu? Or I need to re install all applications that I used in XP on Ubuntu separately? i.e. skype/msn? Outlook? Anyone aware whether the Secure Client application is available for Ubuntu? Thanks!

---

### Post by gunksta on 2008-09-15
> **tech.dummy said:**
> I have currently installed Ubuntu in my laptop (sharing with XP). Is there a way to make the applications shared between the XP and Ubuntu? Or I need to re install all applications that I used in XP on Ubuntu separately? i.e. skype/msn? Outlook? Anyone aware whether the Secure Client application is available for Ubuntu? Thanks!

Given that your questions are very different from the OP (Original Poster), I would suggest that you start a new thread. I do think the folks here will help you, but this thread is not the best place for you to ask this question.

Forums like this typically have only one "topic" per thread. The person who starts a thread is called the Original Poster, usually referred to as the OP. In this case, the OP is having a hard time getting his wireless card to work with Ubuntu. Your questions are quite different and I think you will get more answers in a new thread.

Since you're already a member, it's real easy. Go to the section of the forum that you think you should use (Absolute Beginner Talk would be a good suggestion) and start a new thread.

Enjoy and good luck.

---

