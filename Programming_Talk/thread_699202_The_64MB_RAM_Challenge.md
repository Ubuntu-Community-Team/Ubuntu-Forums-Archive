---
title: "The 64MB RAM Challenge"
date: 2008-02-17
forum: Programming Talk
---

### Post by pmcastillo on 2008-02-17
I'm planning to make a java programming environment under slow computers.... 64MB RAM at max.... I've finally got all the pieces that I need

OPERATING SYSTEM: Xubuntu
DATABASE MANAGEMENT SYSTEM: MySQL

(I'm not sure if Xubuntu could run under 64MB RAM, do you have anymore suggestions? Fluxbuntu? Puppy Linux? Ubuntulite? Damn Small Linux?)

My last problem is. a good Java IDE that has a GUI Builder (SWING or AWT)... I know there's Netbeans, but it eats 512MB RAM. I need something that should fit in 64MB....

---

### Post by jrusso2 on 2008-02-17
If you install to the hard drive Puppy or Damn Small should be able to run on that but launching apps is going to be slow.

---

### Post by public_void on 2008-02-17
Have a look at Java [CLDC]("http://java.sun.com/products/cldc/") and [MIDP]("http://java.sun.com/products/midp/"), even though both are for mobile devices they should prove idea for resource limited machines, especially the CLDC.

---

### Post by geo909 on 2008-02-17
Another light-ubuntu distro.
That one seems to be really light, though:

[http://news.softpedia.com/news/First-look-CrunchBang-A-faster-Ubuntu-77535.shtml]("http://news.softpedia.com/news/First-look-CrunchBang-A-faster-Ubuntu-77535.shtml")

---

### Post by Shin_Gouki2501 on 2008-02-17
geo909 looks interesting!
can you tell some diffrences towards fluxubuntu?!
If u had some personal experience that would be great.

---

### Post by geo909 on 2008-02-17
> **Shin_Gouki2501 said:**
> geo909 looks interesting!
can you tell some diffrences towards fluxubuntu?!
If u had some personal experience that would be great.

Sorry to say that I haven't tried it.. 
It's just looks lighter than Xubuntu or anything similar but who knows..

I actually don't have any old PCs to mess up a little with light distros and that's pretty frustrating because I would really like to! I was thinking about Virtualbox but I would spend more time configuring Virtualbox itself than the OS.... Resurrecting your grandma's PC would be the real deal!!

 I have messed a little bit with Puppy Linux. Not a hard drive installation, just the live thing and I must say I am really impressed. I assume that it is lighter than any light ubuntu distro, it is build to be light, anyway. Its forums are also full of friendly and responsive people, you should definitely try this out if you're looking for user-friendly light distros.

 Here's a screenshot, running puppy live (sooo fast!).  Youtube runs normally. There's also a descent package manager where you can find many things, a tool for mounting/unmounting storage devices etc, you can see a couple of those in the screenshot.

[[IMG]http://www.imageshack.gr/files/4e2vh1rglfi0kcwsfato_thumb.png[/IMG]](http://www.imageshack.gr/view.php?file=4e2vh1rglfi0kcwsfato.png)

---

### Post by LaRoza on 2008-02-17
Xubuntu won't run.

See the Other OS talk for operating systems that will. There is a sticky on light operating systems.

I would do a base install of Ubuntu (use the alternative disk), install the sun-java6-jdk and vim-full packages.

---

### Post by pmcastillo on 2008-02-17
Thanks guys!

I've finally decided what shall I need: (btw, I forgot to tell that "No CD-ROM Drive", is included in the challange....)

So, I've decided that my OS would be: Damn Small Linux ([http://damnsmalllinux.org/](http://damnsmalllinux.org/))... which is VERY small, it's size is only 50MB, as it also support floppy disk installation...

On the IDE side, I've decided it would be... Eclipse ([http://www.eclipse.org/](http://www.eclipse.org/)) plus the Eclipse Visual Editor Addon ([http://easyeclipse.org/site/plugins/eclipse-visualeditor.html](http://easyeclipse.org/site/plugins/eclipse-visualeditor.html))... as it was stated it could run under 64MB memory... ([http://tarpit.rmc.ca/resources/Tutorial/Eclipse/](http://tarpit.rmc.ca/resources/Tutorial/Eclipse/))

If anymore ideas, please reply... :popcorn:

---

### Post by pmasiar on 2008-02-18
64MB is a challenge for Java? I just read about successful project to build Python in 64 **KB** :-)

---

### Post by Geekkit on 2008-02-18
> **pmcastillo said:**
> If anymore ideas, please reply... :popcorn:

For a Java GUI builder you might want to check out Abeille Forms Designer ( [https://abeille.dev.java.net/](https://abeille.dev.java.net/) ). It probably leaves the smallest footprint (possibly smaller than Eclipse and its plugin). Not sure why you're attempting such a small memory footprint; a development environment really needs oodles of main memory for compiling even if we're only talking about natively compiled code (which in this case we're talking about interpreted/runtime environments).

---

### Post by pmcastillo on 2008-02-18
**[SIZE="5"]ABOUT THE 64MB CHALLENGE[/SIZE]**

Well, It's kinda overkill that I set it on 64MB Challenge, well this roots in my curiousity and challenge. But it all boils down to this word: Efficiency

Well most of the computers here (and also most in our country) are about 128-256MB RAM (that's why Netbeans is not an option), but I'm curious if I can STILL make this computers more efficient ----- this is where my curiousity kicks in. Yes, we STILL have 64MB RAM computers, and yes I STILL want to utilize them, as it will STILL serve its purpose. ----- this is where my challenge kicks in.

Well, if the 64MB Challenge is not logically possible, then I could just simply conclude to myself: "I therefore conclude that 64MB doesn't have enough elbow room to make a good Java GUI Programs. Therefore I'll shift my study to 128MB RAMs..."

Funny as it seems, I'm talking like a "slackware" guy hehe... But this is my first time, being in Linux and I'm writting this essay for the Linux Community...




[SIZE="5"]**I. EFFICIENCY & RESOURCES**[/SIZE]

As it always goes: 

> 	MORE SOFTWARE -> MORE HARDWARE -> MORE COST

But their reply would be something like:

> 	MORE BIG TOOLS -> MORE HARDWARE -> MORE COST -> MORE OUTPUT

Yes, yes. If I have those big tools, I can do more. But what if I just need it for a simple task? Like for example, I need to cut a paper, shall I need a lazer beam? So:

> 	BIG TOOLS' FUNCTIONALITIES (minus) WHAT YOU JUST NEED = WASTED RESOURCES

For example, you want to put a simple caption text under your picture, do you need to buy those big Adobe Photoshop CS3 just to put that text? Or just a simple MS Paint? What if I have a computer that only have 128MB of memory, shall I force myself buying and installing Adobe Photoshop CS3 on my computer?

I still remember so many users complaining about the memory hog Vista. Well if you don't want it, don't use it! Why will you force yourself buying something you don't want? I frequently ask them why they switched to Vista they just simply say, "It looks cool!" After spending so much money upgrading your computer to "reach" the minimum system requirements of Vista, and you just simply want the "looks cool" feature? Well, I could make XP "looks cool" without the resource hog of Vista. ----- Efficiency is getting the most out of your resources.

Others might say, "Well, you might use those yet unused functionalities in the near future". Well take the word: "MIGHT". Today, I don't need that functionalities. In the future, why should I stick and be a martyr with my previous tools? ----- All in all, what I'm saying is: "Getting the right tools for the right job"




**[SIZE="5"]II. EFFICIENCY & TIME[/SIZE]**

Others might say, "Efficiency is what you are talking about? Then use assembly language! It runs smooth as it has no doodads". Like what I said on my previous paragraph, "Getting the right tools for the right job". For example, I want to make a simple "Multiplatform GUI-based Hello World". Shall I tinker with assembly and study the different kinds of OS and spend maybe for 3 months coding? I think this is not anymore efficient, and why should I reinvent the wheel if it is already invented (the multiplatformness of Java). OR I'll just pop my handy-dandy Java GUI Builder and finish it in 3 minutes. ----- Efficiency is not just resources, it is also time.

As conventional as it says, "Try buying this $$$ IDE, you will produce more output in a short period of time". But why not, "Try mastering the skills and techniques with what is freely available IDEs, you will produce more output in a short period of time. Plus you will be more skillful when it comes to under-the-hood problems."




**[SIZE="5"]III. EFFICIENCY & COST[/SIZE]**

This actually happened to me, I was assigned to make a system for the library. It will consist of 5-10 networked computers. Shall I buy those cutting-edge and expesive computers? Or just buy those low-cost computers, and use resource-efficient softwares? ----- Efficiency is also about cost.

Many will say to me, "Get a life! This is 2008! Put that damn old computers to the metal shredder guys, there's alot of cheap computers today!" Well I got a problem with this word: BUY. And also, for example, an employee comes to the office everyday and turns on the computer and just type the handwritten forms for the computer, does he need to get a Quad-Core processor or a Vista just to get the job done? Which is more profitable, getting some money from the scrapped old computer, or the data of what the employee typed?




**[SIZE="5"]IV. EFFICIENCY & USER-EFFORT[/SIZE]**

I'm not saying like, "Ok guys, let's resort to those cryptic command-line programs, as it is efficient in every aspect." Well, it's efficient on the technical-side, but will it be efficient on the user-side? How much effort will the user exert on studying those cryptic command-line programs, and how much effort will the user exert on just clicking his way out?




[SIZE="5"]**V. CONCLUSION**[/SIZE]

SO! Let's use the previous graph, "MORE SOFTWARE -> MORE HARDWARE -> MORE COST" Then replace "MORE SOFTWARE" with "MORE EFFICIENT SOFTWARES":

> 	MORE EFFICIENT SOFTWARE -> LESS HARDWARE -> LESS COST -> MORE OUTPUT! -> AND MORE ROOM FOR OUTPUT!

*I'll end my essay here: "If you are assigned to shoot a glass bottle, will you use a bazooka to bomb your target or just a quick pistol will do?"*

*[SIZE="1"]*pmcastillo then hides in the corner, in fear of getting screamed at hehe* ^_^[/SIZE]*

---

### Post by LaRoza on 2008-02-18
Java works on low resource machines, after all, kitchen appliances use it, as do all Blu-Ray players.

Java will work on that machine, however, if you want to use large and resource hungry applications on it you are doomed to fail.

I recommended a base install of Ubuntu and using a console editor. 

I imagine that the machine would be fast with this.

You can use GUI programs, I recommend a light editor, rather than a bloated IDE. You can install a WM like Fluxbox and use a GUI editor to write Java GUI programs. 

I wish I had a spare computer (any x86) to use.

---

### Post by pmcastillo on 2008-02-18
* pmcastillo then pops out from the corner * seems no one scream at me..:lolflag:

> 
Java works on low resource machines


Yah ^_^ That's why I'm thinking java on low resource computers... ^_^

> 
if you want to use large and resource hungry applications on it you are doomed to fail.


I've noticed, there's only a few of big java applications:

Netbeans
Limewire
Firefox

BTW, why making big applications in Java are doomed to failure? Is it because JRE + Your Application = More RAM?

> 
I recommend a light editor, rather than a bloated IDE


Yah, that's what I'm researching ^_^

> 
I wish I had a spare computer (any x86) to use.


Thanks dude! :tongue:

---

### Post by LaRoza on 2008-02-18
> **pmcastillo said:**
> 
BTW, why making big applications in Java are doomed to failure? Is it because JRE + Your Application = More RAM?



I meant, big apps on that computer will fail. So running IDE's and large applications won't work well.

---

### Post by JamesUser on 2008-02-18
I would suggest Fluxbuntu. It's very lightweight. I recently installed it on my spare machine... A PIII and max. 128 MB RAM (Not sure, it could be lesser. But not more). I didn't use it for any programming though. I use it to rip DVD's while my primary pc remains available for use.

My gut feeling is fluxbuntu will do. And I don't use IDE's for developing simple applications. Just use any text editor with syntax highlighting. My 2 cents.

---

### Post by kerry_s on 2008-02-18
wow, nice essay.

you should go custom then, you can get the best of everything, mold it to your needs.

i recommend debian for older systems, it's easy to use apt-get and get anything you want. if you choose wisely it can run on anything.
[http://cdimage.debian.org/debian-cd/4.0_r2/i386/iso-cd/debian-40r2-i386-businesscard.iso](http://cdimage.debian.org/debian-cd/4.0_r2/i386/iso-cd/debian-40r2-i386-businesscard.iso)

 [http://forums.debian.net/viewtopic.php?t=13828](http://forums.debian.net/viewtopic.php?t=13828)

my systems is 450mhz 256 ram, so i build her to work with in those limits. i usually start like this.->

use the net installer
base install, at the selection screen uncheck both selections.
apt-get install xorg jwm mc rox-filer
reboot(ctrl+alt+delete)
log in as the user and type> startx < launch the terminal/terminal's, then continue building. i usually start mc first and set a solid background in my ~/.jwmrc (cp /etc/jwm/jwmrc ~/.jwmrc) (<Background type="solid">black</Background>)(close,click restart)

yes, it's that simple.
jwm = my preferred, light weight window manager, it takes learning, but is really flexible once you figure out what you can and can't do. it can be set up any way you want.
rox-filer = gui file-manager
mc = is a terminal file manager and editor, it's actually all you need if you want light.
terminal = i'm using xterm, it's installed as part of xorg
gui editor = i'm using xedit, it's also a part of xorg, leafpad is another light option, but you have to install that.
feh = for images
xcalc = calculator, part of xorg, so it's already there
paint = mtpaint
docs = abiword
pdf = epdfview
music & video = vlc, while not light, it does it all
web browser = iceweasel, not light, but if it can run is the best choice.

a custom install takes practice to get it just right, but the benefits are well worth the time you put into it to get a system that fits your needs and works in the limits of the system.

the pic's
i'm using my kde style setup. :)
forgot to mention on startup it's only using 24mb ram.

---

### Post by pmasiar on 2008-02-18
Another project worth looking at might be Android: Google's reimplementation of JVM for mobile phones. They choose to implement naw system using Java the language but not using JVM, (IIRC called dalek): design it to conserve resources and be more optimizable than JAVM implementation is.

---

### Post by Fbot1 on 2008-02-18
I suppose you could use busybox's vi.

---

### Post by jespdj on 2008-02-18
> **pmasiar said:**
> 64MB is a challenge for Java?
No, it isn't. :rolleyes:

---

### Post by Shin_Gouki2501 on 2008-02-18
> **pmasiar said:**
> 64MB is a challenge for Java? I just read about successful project to build Python in 64 **KB** :-)

[http://www.javaunlimited.net/contests/java4k.php](http://www.javaunlimited.net/contests/java4k.php)

---

### Post by pmasiar on 2008-02-18
Yes, but I do not see how this is relevant. Java 4K does not include the JVM, IIUC, just 4K of java bytecode to run the game. Python64K does include big chunk of core Python.

---

### Post by Geekkit on 2008-02-18
> **pmasiar said:**
> Yes, but I do not see how this is relevant. Java 4K does not include the JVM, IIUC, just 4K of java bytecode to run the game. Python64K does include big chunk of core Python.

Are you referring to the tinypy project?

---

### Post by pmasiar on 2008-02-18
> **Geekkit said:**
> Are you referring to the tinypy project?

I refer to [this project](http://www.philhassey.com/blog/2008/01/10/64k-tinypy-now-with-vm-included/) Yes, it might be tinypy.

---

### Post by Geekkit on 2008-02-18
> **pmasiar said:**
> I refer to [this project](http://www.philhassey.com/blog/2008/01/10/64k-tinypy-now-with-vm-included/) Yes, it might be tinypy.

I've tried this project before. It is leaner than the usual Python runtime but still requires several megabytes of memory (when I ran the julia.py example, it required anywhere from 4 MB to 20 MB depending on where it was in execution) for its runtime environment. No program requiring a interpreted runtime environment (PHP, Java, .NET, Python, etc.) can get away with 64 KB of main memory including its runtime memory footprint - not even J2ME that is burned into the ROMs that come with mobile phones (e.g., Nokia's implementation for example). Especially not with the requirements of today's interpreted runtimes (JIT compiling, GUIs, draw buffers, garbage collection, etc.).

Shin_Gouki2501's post is quite relevant since it is an apples-to-apples comparison.

---

