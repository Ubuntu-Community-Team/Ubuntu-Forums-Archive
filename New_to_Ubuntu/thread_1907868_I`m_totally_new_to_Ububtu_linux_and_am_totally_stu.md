---
title: "I`m totally new to Ububtu linux and am totally stuck!"
date: 2012-01-12
forum: New to Ubuntu
---

### Post by cliveT on 2012-01-12
Hi I am totally new to Any "Linux" operating system and have installed Ubuntu 11.10 as a dual boot on windows 7-64 bit - just to have a look and try it out!
 
Straight away I like the look and feel already and I can see me staying with it if only I can get my head around how to install additional programs, I have always been used to just click,click, click in windows but in Ubuntu I am totally stuck!
 
I`ve had a look on the Ubuntu website in the "support" section and have read the "How to" if you like (see below)
 
**Install other repositories**
 

[LIST=1]
[*]<LI class=steps>Click on the Ubuntu Software Center icon in the Launcher, or search for Ubuntu Software Center in the search bar of the Dash.
<LI class=steps>When the Software Center launches, click Edit> &#9656; Software Sources
<LI class=steps>You will be asked to enter your password. Once you have done that, switch to the Other Software tab.
<LI class=steps>Click Add and enter the APT line for the repository. This should be available from the website of the repository, and should look similar to:
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick main
[*]Click Add Source then close the Software Sources window. Ubuntu Software Center will then check your software sources for new updates.
[/LIST]1.But when I click on the software centre I can`t find the Edit>software sources anywhere - where is the Edit button?
 
2.What is the "APT" line?
 
3. What is a repository?
 
As you can see I am totally new to all of this and would very much like to learn. I would like to install QCAD Pro version on this Ubuntu (which is available for Windows, Mac and _Linux_) but just dont know where to start. I have been used to just using the windows installer - is there an installer I should be using in Ubuntu?
 
Regards
 
Clive:)

---

### Post by Anuovis on 2012-01-12
Hello,

There are many ways how to install programs on Ubuntu, using Terminal, using various package managers like Synaptic but the simplest graphical way is just to go to the Ubuntu Software Center and click Install. 

You will be prompted for the password and once that is in, it should do all the work automatically. No need to fiddle with repositories if the application already shows up in the Software Center.

If you ever need to add repositories (It's like a storage on the net with your software and future updates that Ubuntu will use), you can add them via the Software Sources as you said. The Edit menu (as all other menus in Ubuntu 11.10) are hidden. Hover your mouse over the title of the window, on the top panel. It will be revealed. 

Be careful what you add though.

---

### Post by cliveT on 2012-01-12
Thanks Aunovis
 
Assuming I get that far how do I then add a new repository?

---

### Post by Anuovis on 2012-01-12
Adding a new repository is easy, just go the *Other Software* tab. Attaching a screenshot. You must know the correct link though.

What is it exactly you are trying to install? I have found QCad in the Software Center, is that the thing you are looking for?

---

### Post by lechien73 on 2012-01-12
Hi & welcome to Ubuntu and the forums,

Well done for taking the plunge to try out Linux! As stated, if you hover over the title bar in Software Centre (or press Alt+E), the **Edit** menu will appear. Choose **Software Sources**, click on the **Other Software** tab and click the **Add** button. Enter the repository details - these are usually on the website of the program you want to install.

With regard to apt - it is useful to master the command line, so this might help you with regard to using apt-get to install software [https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)

Finally, QCAD is available directly from the Software Centre, so just search there for QCAD and then hit the **Install** button.

---

### Post by cliveT on 2012-01-12
Anuovis & lechien73
 
thanks for your quick replies, yes QCAD is there but its the community (free) version. I want to install the Pro version
 
see - [http://www.qcad.org/qcad3.html](http://www.qcad.org/qcad3.html)
 
It also states that 
 
*[SIZE=2]* Some additional 32bit libraries may have to be installed in order to run the QCAD 3 32bit binary under a 64bit platform. openSUSE 11.4 64bit requires a package called "Mesa-32bit" to be installed. [/SIZE]*
*[SIZE=2]** Package "ia32-libs" must be installed.[/SIZE]*
*[SIZE=2][COLOR=#808080][/COLOR][/SIZE]* 
I wouldn`t know how to install these extra "ia32-libs" if needed?

---

### Post by lechien73 on 2012-01-12
You can open a terminal window and type:

```
sudo apt-get install ia32-libs
```

You will be asked for your password - it will be invisible when you type - and the cursor won't move.

Have you already purchased QCAD, and so have access to their downloads area? Ideally you would want to download a .deb file, which you can install by just double clicking on it.

---

### Post by Anuovis on 2012-01-12
You might also try Synaptic (needs to be downloaded from Software Center) for individual packages. It provides a graphical way to add and remove them.
Terminal is a good tool and you might want to learn a thing or two about it but Synaptic can also be good if the command line looks intimidating at first.

And yes, .deb files work much like setup.exe files in Windows. If you have a choice, always pick one as it simplifies things quite a bit. A simple double click will do the job.

---

### Post by cliveT on 2012-01-12
yes I have already purchased QCAD so I can download from "download" area - where do I save it to?

---

### Post by cliveT on 2012-01-12
Also out of curiosity how do I open a terminal window?

---

### Post by lechien73 on 2012-01-12
The forum seems to be getting hit with a lot of spam today :mad: anyway, to open a terminal window, press Ctrl+Alt+T, or you might have a black icon with a white ">_" in the side bar. Alternatively, press Alt+F2 and type *terminal*

You can save the file to wherever you want - the Desktop, your home folder or the Downloads folder. As long as you remember where it is and you can find it again later ;)

---

### Post by androssofer on 2012-01-12
> **cliveT said:**
> 
yes I have already purchased QCAD so I can download from "download" area - where do I save it to?

Also out of curiosity how do I open a terminal window?

look for the .deb file as mentioned earlier. then save it somewhere handy. I usually put stuff like that in my 'Downloads' folder. then open the downloads folder, double click the deb file and it will install for you.

to get a terminal window: click the ubuntu logo on the top left and type 'terminal' and it should appear :-).

or press 

ctrl   alt   T 

and it should open

---

### Post by cliveT on 2012-01-12
Hi Guys thankyou for all your help so far!
 
Right I have downloaded the qcad-3.0.0-rc2-prof-linux.bin (is this the deb file mentioned?) to my memory stick and from here I have copied this to my desktop - now what do I do to install this?
 
The other thing I want to ask is if I go the software centre route  (which I would prefer to do!)- and try to add a new repository source - where do I find the APT line of the repository that i want to add?
 
Regards
 
Clive

---

### Post by Zoot 10+six on 2012-01-12
> **cliveT said:**
> Also out of curiosity how do I open a terminal window?

Hi Clive,
         I too am new to ubuntu, installed it the other day. I am just getting my head round the terminal, from the little I know you open the terminal window by pressing ctrl-alt-T on your keyboard. I bought a couple of books to help me learn about Linux, but they will only be useful to me after I have a couple of months experience working with the OS. The best place I have found for advice is here in the forums.....Good luck, Paul.

---

### Post by lechien73 on 2012-01-12
> **cliveT said:**
> Hi Guys thankyou for all your help so far!
 
Right I have downloaded the qcad-3.0.0-rc2-prof-linux.bin (is this the deb file mentioned?) to my memory stick and from here I have copied this to my desktop - now what do I do to install this?
 
The other thing I want to ask is if I go the software centre route  (which I would prefer to do!)- and try to add a new repository source - where do I find the APT line of the repository that i want to add?

Cool...so, now that you have it on your desktop, right click on the file and choose properties. Click the **Permissions** tab - like in the attached screenshot - and check the box that says **Allow executing file as a program**.

Now open a terminal window and type:

```
sh ~/Desktop/qcad-3.0.0-rc2-prof-linux.bin
```

I've never installed QCAD, so I don't know exactly what the .bin file will do, but try this and see what happens :)

---

### Post by cliveT on 2012-01-12
do I type exactly this - sh ~/Desktop/qcad-3.0.0-rc2-prof-linux.bin, if so where do i find the "squiggly" symbol after sh on my keyboard?

---

### Post by lechien73 on 2012-01-12
Hmmmm...depends on your keyboard layout. On mine, it's above the # symbol, next to the return key.

You could just copy and paste the exact command from the post into your terminal. Select the command, right-click and copy, and then right click on the terminal window and select Paste :)

---

### Post by cliveT on 2012-01-12
ok - I found the "squiggly" symbol - ha ha!
Anyway I typed in what you said and I get a return in the terminal saying -no such file or directory?
I must be doing something wrong here I think.
 the terminal line starts [EMAIL="clive@ubuntu:~$"]clive@ubuntu:~$[/EMAIL] then I type exactly - sh ~/Desktop/qcad-3.0.0-rc2-prof-linux.bin, then I press the enter key on my keyboard and then I get the return mentioned already in the terminal.

---

### Post by lechien73 on 2012-01-12
Ok, let's try a slightly different way. The file is copied to your desktop, so that means it's in the Desktop directory. The squiggly ~ symbol is a shortcut for your home directory.

So, try:

```
sh ~/Desktop/qcad
```

Before pressing enter, press the Tab key. This will auto-complete the filename, since I may have reproduced it incorrectly. I'm presuming you didn't put it in a subfolder on the desktop? And I'm also presuming that you made it executable, as per a previous post.

---

### Post by cliveT on 2012-01-12
pressing the tab key does nothing?

---

### Post by cliveT on 2012-01-12
ok I`ve done it! I just entered Desktop/qcad without entering the sh~,then I pressed the tab key and it completed the rest.
 
Right now I will run it and see if it runs alright.

---

### Post by cliveT on 2012-01-12
I know the program is installed and I have the Icon on the desktop, but nothing happens when I click on it?
 
I must be missing something?
 
How do I look into the programs files?

---

### Post by cliveT on 2012-01-12
OK I`ve worked it out!
I rememberd that I needed to download the 32 bit libs as mentioned earlier from the QCAD website "down-load" area, so I`ve done this and all is well now - at last its installed.
 
I truly hope all installs are not like this!
 
My thanks to you Lechien73 and Anuovis for your excellent input - guys its good to know that this forum is well supported by people as committed like you.

Regards and thanks again 
 
Clive
 
Now I am going to sleep as I am worn out with all of this.
 
Once last thing guys (ha ha) do you need to use an Anti-virus program or firewall with Ubuntu?

---

### Post by lechien73 on 2012-01-12
Glad you got it sorted :) I'm going to bed too!!

Firewall is a good idea, but I've never used anti-virus with Linux. It's one of the lovely freedoms I enjoy :D

If you're happy with the fix, then please could you click on the **Thread Tools** menu at the top and mark it as [SOLVED]? Enjoy!!!

---

### Post by Zoot 10+six on 2012-01-12
> **cliveT said:**
> OK I`ve worked it out!
I rememberd that I needed to download the 32 bit libs as mentioned earlier from the QCAD website "down-load" area, so I`ve done this and all is well now - at last its installed.
 
I truly hope all installs are not like this!
 
My thanks to you Lechien73 and Anuovis for your excellent input - guys its good to know that this forum is well supported by people as committed like you.

Regards and thanks again 
 
Clive
 
Now I am going to sleep as I am worn out with all of this.
 
Once last thing guys (ha ha) do you need to use an Anti-virus program or firewall with Ubuntu?

Hi Again Clive,
               If you want to know all you need about a firewall go to my question post-"Is there a firewall in Ubuntu 11.10". Just go to the bottom right of the page in beginner talk, and go to page 15 and look for my post (title above) and search for the post started by me-Zoot 10+six. You will find all you need to know there, I sorted my firewall before downloading any software, as when you do your ports are open to hackers getting onto your PC.....Good luck, Paul.

---

### Post by whyDerrick on 2012-01-12
> **cliveT said:**
> OK I`ve worked it out!
I rememberd that I needed to download the 32 bit libs as mentioned earlier from the QCAD website "down-load" area, so I`ve done this and all is well now - at last its installed.
 
I truly hope all installs are not like this!
 
My thanks to you Lechien73 and Anuovis for your excellent input - guys its good to know that this forum is well supported by people as committed like you.

Regards and thanks again 
 
Clive
 
Now I am going to sleep as I am worn out with all of this.
 
Once last thing guys (ha ha) do you need to use an Anti-virus program or firewall with Ubuntu?
Hey cliveT,

As another new user, I can promise you that not all installs are anywhere near as complicated. Installs from the software center and synaptic package manager are often a breeze. When you go out of them, you have to pull some weight and either show what you know or show what you've learned :)

Good luck.

---

### Post by cliveT on 2012-01-13
ok thankyou to everyone who has helped me to get started - I slept last night like a dog!

---

### Post by cliveT on 2012-01-13
aaa

---

### Post by nothingspecial on 2012-01-13
> **cliveT said:**
> aaa

?

---

### Post by cliveT on 2012-01-13
aaa doesn`t mean anything - I typed aaa my mistake and posted it, I couldn`t see how to delete the post!

---

