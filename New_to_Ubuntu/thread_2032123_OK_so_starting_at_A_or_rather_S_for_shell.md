---
title: "OK so starting at A or rather S for shell"
date: 2012-07-23
forum: New to Ubuntu
---

### Post by Jackalyn on 2012-07-23
It seems like to really understand what I am doing I need to learn the lingo. Bear with me this is like being a kid and scribbling and somewhere along the line kids misunderstand stuff but it might help others like me who are completely ignorant and do not have time to go to college and do course whatever in linux.

I know GUI is graphical User interface,  Is that the screen and all the stuff on it?

Is Shell a bit like a book cover? 

So a *Bash* shell is like a version of the book you need with the instructions on how to do it in it? BUT you can write in the book and unlike a book it will do what you tell it. In a way, you can write the story in the book and the book will become a reality doing what you told it as long as you tell it in the language the shell  book understands.

Like you join up dots and you get a picture that is recognisible?

And you have other shells. Some shells use different programming languages to others?

(I kind of know there are different programming languages and was told by my ex (who i probably right I would never understand how to write a programme ...that there is C and C+ and C++ -he writes the things.   Who knows what a kid who has not talked yet can do?)

Shells can be compatible and have bits of the language in one shell read by another shell. There is a Korn shell and a C shell and they can understand each other as well as the bin shell and the bash shell. Like a load of us can all understand "bonjour,"" hello,"" hi," and "salaam aleykum."

  POSIX is a** P**ortable[COLOR=black] **O**[/COLOR]perating **S**ystem Interface  and just means a set of standards set by the

 IEE who are the** I**nstitute of **E**lectronics **E**ngineers (and live in New York presumably in  one of those big sky scraper thingys.)

So if it is POSIX compliant what happens can happen and be read by say Windows *and* Linux.

(Therefore for example, Firefox could open in either.- Because the writing in the shell can read the 'writing' on the internet needed to open firefox as it were.)

(A shell can both accept and carry out (execute) commands.

So in a sense, if you know the language you can make up a story which  you can put in a shell and it will act out the story.

These 'stories' are called scripts and some might already be written in the shell and you can add your own as long as it is in the right language.

So some commands are already inside the shell (*builtin*) like [I]break and exec  (I know exec will be execute(carry out) but break? 

[/I]Shells have **I/O** streams and that is easy because it means **I**nput and **O**utput streams. They have 3 of themThere is a standard input, a standard out put and a standard error. So you know if you put it in, if it came out and if you got it wrong.So if you write something in the terminal each time you hit the keys it is called a terminal keystroke?What you write into the terminal is called an input stream - like you are writing a story and the terminal hears it- output stream unless you get it wrong in which you are told you have lost the plot.

The terminal is the window you get by typing in t into the dashboard home and clicking on the terminal (sure there is an easier way but bear with me!) 

In other words you send instructions to the terminal (which is obvious even  to me but this is the ABC of linux)

There are things called shell prompts, Unless you know what this is you are not going to B.

---

### Post by Jackalyn on 2012-07-23
A shell prompt is the line where you type the command. 

So I think that when I open the terminal where I am told to write is the shell prompt?

(Can't see I need to know more than that at this stage of  the game.)

End of [http://www.ibm.com/developerworks/linux/library/l-lpic1-v3-103-1/index.html](http://www.ibm.com/developerworks/linux/library/l-lpic1-v3-103-1/index.html) Going to 

[http://www.ibm.com/developerworks/linux/tutorials/l-basics/](http://www.ibm.com/developerworks/linux/tutorials/l-basics/)

Sometimes you need to log in to things and become the root of things like planting a new seed from a plant that shed its seeds. You get new roots but the same plant, in order to download some things you may want via the software console.

In which case you have to put stuff into the terminal.

There are different desktops and what you get is what you installed so if you installed Ubuntu you get a Gnome desktop but another install of linux might be Fedora and so on. Just in a sense a name of your desktop on your PC once you installed it.

[http://www.ibm.com/developerworks/linux/tutorials/l-basics/section2.html](http://www.ibm.com/developerworks/linux/tutorials/l-basics/section2.html)

I don't think we need to go through that. Most of us can log in and the info is easy enough to understand. Seems to me that Linux has lots of different versions and it is safer to stay with Ubuntu for now but that Suse and KDE and all that are different forms of linux - like you get English people from  Surrey, Yorkshire and Lancashire bthey are all able to understand each other but definitely different. In a sense all I need to know is they are different desktops and will work slightly differently.

Whichever terminal it is you have is your shell and the way you get command line access is to open it then you can play around putting stuff in it and seeing what you get.

[http://www.ibm.com/developerworks/linux/tutorials/l-basics/section4.html](http://www.ibm.com/developerworks/linux/tutorials/l-basics/section4.html)

OOH a clock would be useful. Just typing in xclock does not produce a clock!

OOOOOOH yes it does! I have a clock! It can tell GMT time. I wonder if it will stay if I close the terminal?

Another name for a shell might be an interpreter. 

(It is just nice to know what people are talking about)

[http://www.ibm.com/developerworks/linux/library/l-lpic1-v3-103-1/index.html](http://www.ibm.com/developerworks/linux/library/l-lpic1-v3-103-1/index.html)

---

### Post by mastablasta on 2012-07-23
> **Jackalyn said:**
> I don't think we need to go through that. Most of us can log in and the info is easy enough to understand. Seems to me that Linux has lots of different versions and it is safer to stay with Ubuntu for now but that Suse and KDE and all that are different forms of linux - 
 
 
wrong SUSE, Fedora, RedHat, CentOS, Debian, Slackware... are all different distributions of linux. you can check more of them here: [http://distrowatch.com/](http://distrowatch.com/) it's a nice site offering quick reviews and describing differences betwen them.
they all use Linux Kernel but they use different modules and do things differently.
Safer to stay with Ubuntu? no not really. Red Hat and Debian excell at stability. Fedora is excelent for new hardware as is Arch (which is roling distribution or distro in short). Ubuntu is very user friendly but so are some other distributiuons such as Netrunner, PCLinuxOS, ZorinOS, Mageia, Linux Mint...
you also have a couple of super light ones for old mashicnes (slitaz, Puppy) and a few that are firewall, specilised in servers or kiosk devices etc.
 
then you have various desktop environments (and windows managers) you can install to use them as desktops such as KDE, Gnome, XFCE, LXDE, Openbox, IceWM, E17...
 
Then you can have different respins of distribution with different default environment.
For example Ubuntu uses Gnome3+Unity interface, while Kubuntu uses KDE and Xubuntu uses XFCE...
 
They all have Ubuntu underneath but use different desktop environment to present themselves.
 
 
regarding you terminal quesitons i found it is explained nicelly in ubuntu manual (see my signature) or read the free e-book found here: [http://linuxcommand.org/](http://linuxcommand.org/)
i find it explains nicely the basics with some excercises to joggle your mind.
and here is the page on terminal/shell/bash to get you started: [http://linuxcommand.org/lc3_lts0010.php](http://linuxcommand.org/lc3_lts0010.php)

---

### Post by nothingspecial on 2012-07-23
Hi Jackalyn,

The default shell in Ubuntu is bash.

[[COLOR="Magenta"]Here[/COLOR]]("http://mywiki.wooledge.org/BashGuide") is a nice guide aimed at beginners.

---

### Post by Jackalyn on 2012-07-23
> **nothingspecial said:**
> Hi Jackalyn,

The default shell in Ubuntu is bash.

[[COLOR=Magenta]Here[/COLOR]]("http://mywiki.wooledge.org/BashGuide") is a nice guide aimed at beginners.

Thanks guys - I just got a bit sick of reading things with shorthand in and not quite understanding some replies because they were too technical.  Even the beginners guide I was reading still assumed I would know some terms, Even if  *I knew what it stood for that did not mean I knew what it was or what it did.*

On the other hand do you know what EYFS stands for - no probably not unless you are a child care worker in the UK. -every thing develops its own shorthand.

---

### Post by nothingspecial on 2012-07-23
> **Jackalyn said:**
> Thanks guys - I just got a bit sick of reading things with shorthand in and not quite understanding some replies because they were too technical.  Even the beginners guide I was reading still assumed I would know some terms, Even if  *I knew what it stood for that did not mean I knew what it was or what it did.*

On the other hand do you know what EYFS stands for - no probably not unless you are a child care worker in the UK. -every thing develops its own shorthand.

:)

I suppose everything is a little like that when you are new to it. Looking through your posts, you've been a little unlucky with your hardware. Some people install Ubuntu and everything works. They never have to worry about a terminal or what a shell is. I think it's great you are asking questions and reading stuff about it. On the other hand, you don't need to.

---

### Post by Paqman on 2012-07-23
> **Jackalyn said:**
> 
On the other hand do you know what EYFS stands for - no probably not unless you are a child care worker in the UK. -every thing develops its own shorthand.

Or you've got young kids of your own: Early Years Foundation Stage ;)

If you need people to explain the jargon a bit, don't hesitate to ask. People are pretty helpful and friendly round here, but it's easy to lapse into gobbledegook when you're trying to explain things.

---

### Post by Jackalyn on 2012-07-23
> **Paqman said:**
> Or you've got young kids of your own: Early Years Foundation Stage ;)

If you need people to explain the jargon a bit, don't hesitate to ask. People are pretty helpful and friendly round here, but it's easy to lapse into gobbledegook when you're trying to explain things.

:P Well I did think the UK people might understand.

Seriously though this happens everywhere - We assume that things are obvious when they are not. So for example  earlier I read a thread that asked about a GUI where it was obvious the person was as clueless as me and someone had replied with what would then have seemed like gobbledeygook.

For beginners it needs to be as simple as the first building block and not assumed. 

I will still stick to Ubuntu as it is my comfort blanket but one day I will maybe pick up Red Hat purely as it sounds a bit like Dr Seuss.:popcorn:

---

### Post by Jackalyn on 2012-07-23
> **nothingspecial said:**
> :)

I suppose everything is a little like that when you are new to it. Looking through your posts, you've been a little unlucky with your hardware. Some people install Ubuntu and everything works. They never have to worry about a terminal or what a shell is. I think it's great you are asking questions and reading stuff about it. On the other hand, you don't need to.

Oh yes I do lol...I like messing around with stuff even if it is new and I have no clue.

Yep the hardware has been an issue but I think often there is a solution. I keep telling people about Sakis3g as that works so well now I have it. 

Most of the time if it is step by step things work where there is a solution but when it is assumed you have the steps that is tricky.

---

### Post by nothingspecial on 2012-07-23
> **Jackalyn said:**
> We assume that things are obvious when they are not. So for example  earlier I read a thread that asked about a GUI where it was obvious the person was as clueless as me and someone had replied with what would then have seemed like gobbledeygook.

For beginners it needs to be as simple as the first building block and not assumed. 



I agree, but like Paqman said, it's easy to lapse into gobbldygook. Just ask if you don't understand anything :)

---

