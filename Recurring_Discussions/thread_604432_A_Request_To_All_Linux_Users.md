---
title: "A Request To All Linux Users"
date: 2006-06-28
forum: Recurring Discussions
---

### Post by crhylove on 2006-06-28
How about a way without command line?  Seriously.  What year is this?

---

### Post by aysiu on 2006-06-28
[QUOTE=crhylove]How about a way without command line?  Seriously.  What year is this?[/QUOTE]
It's 2006, and I'm not offering VNC-guided phone support. I'm doing online support with text. The command-line is perfect for that.

What's easier?

This? > Paste this command into the terminal and then show me the output: ```
sudo fdisk -l
```

or this? > Go to System > Administration > Synaptic Package Manager. Click the Reload button. Then click Find. Then do a search for *gparted*. Right-click it and mark it for installation. Click Apply. Close Synaptic Package Manager.

Go to Applications > System Tools > GParted and then press the print screen button. This will launch gnome-screenshot. From gnome-screenshot, save the screenshot of the GParted screen to the desktop. If you have more than one hard drive, be sure to click the upper-right-hand corner of the GParted window to select the other drive and do a screenshot for that.

Then upload your screenshots to these forums so I can look at them. By the way, the second set of instructions would have to be modified heavily for Xubuntu and Kubuntu. The first set of instructions would work for all three.

If you have nothing constructive to say, why are you posting here? Does your smarmy remark help anyone get write permissions to an external hard drive? Can I ask you how many screenshot-heavy tutorials you've created lately?

---

### Post by anantshri on 2007-11-06
This request is specifically to all so called linux expert's or the person's who are giving answers to the queries in any of the forum.

DO WE NEED TO TELL SUCH LENGTHY COMMANDS TO USERS, if the same task could be done in a fe click's

coz it creats a sort of confusion

like i read some where in this forum only 

tar xzvf xyz.tar.gz

error came as file not found and the person was in complete state of panic,

what the expert could have told the person is that you just need to locate file using your explorer (nautilus here) and then can ritht click on it to extract the files.

and open the directory to view its contents

also if you wish you can execute the commands by doubleclicking on them.



THE WHOLE AIM OF THIS POST IS TO CREATE AN AWARENESS AMONG USERS THAT THE MAIN CAUSE WHY PEOPLE FEAR TO COME TO LINUX IS ITS EXTENSIVE USAGE OF COMMANDLINE.


firstly let them work on graphical mode and get them comfortable with other applications, then tell them what you have been doing with graphical environment could also be done using console.

so that they don't have a kind of phobia to linux as a whole.

THIS IS WHAT I HAVE LEARNED IN THE PAST SIX YEARS OF MY LINUX EXPERIENCE.

if any body has any kind of suggestion or critisism then do post it in.

---

### Post by M4VE on 2007-11-06
There was an old school of thought in the linux world that a person should have to know how the nuts and bolts make up the greater picture before moving on to the fast food approach to computing.  Nobody has ever claimed linux to be an OS of the masses, it's strength isn't in usability, or simplicity, but in flexibility and adaptability to many uses.  Your job as a user shouldn't be to convert as many people as possible to linux, because if you did that, and enough attention was drawn to it, it would eventually be clouded and corrupted with the same problems as all other operating systems.  Anyway, that's my two cents worth.

---

### Post by popch on 2007-11-06
I think we all agree that different users might have different preferences and needs.

Some of the people here are so friendly as to tell the less expererienced users what commands to use, and when to use them. I suggest they continue doing so, or rather, I beg them to.

On the other hand, if you think you can help users better, faster or to more lasting effect by describing to them in sufficient detail how to do what they need using the GUI, please help those users who may profit more by your method.

Mod: can we have a recurring recurring discussions sub-subforum?

---

### Post by Nano Geek on 2007-11-06
> **anantshri said:**
> This request is specifically to all so called linux expert's or the person's who are giving answers to the queries in any of the forum.

DO WE NEED TO TELL SUCH LENGTHY COMMANDS TO USERS, if the same task could be done in a fe click's

coz it creats a sort of confusion

like i read some where in this forum only 

tar xzvf xyz.tar.gz

error came as file not found and the person was in complete state of panic,

what the expert could have told the person is that you just need to locate file using your explorer (nautilus here) and then can ritht click on it to extract the files.

and open the directory to view its contents

also if you wish you can execute the commands by doubleclicking on them.



THE WHOLE AIM OF THIS POST IS TO CREATE AN AWARENESS AMONG USERS THAT THE MAIN CAUSE WHY PEOPLE FEAR TO COME TO LINUX IS ITS EXTENSIVE USAGE OF COMMANDLINE.


firstly let them work on graphical mode and get them comfortable with other applications, then tell them what you have been doing with graphical environment could also be done using console.

so that they don't have a kind of phobia to linux as a whole.

THIS IS WHAT I HAVE LEARNED IN THE PAST SIX YEARS OF MY LINUX EXPERIENCE.

if any body has any kind of suggestion or critisism then do post it in.A couple of reasons why the CLI (Command Line Interface) is better than the GUI (Graphical User Interface):
[LIST]
[*]It is much easier to say "Copy and Paste this" than to say "Click here, then click here, then right click here, then press this button..."
[*]It teaches the guy asking the question a little more about Linux, which is always good.[/LIST]

---

### Post by anantshri on 2007-11-06
i AM NOT HERE DEBATING A TOPIC ON IS CLI BETTER THE GUI OR VICEVERSA

I have also been avid user of linux, i agree it was not for masses but don't you think bu just putting up your thought that it is  not and was not for masses, you have defied the basic aim of UBUNTU. (Linux for human beings)


well we can leave that.

and yes as far as being copy and paste friendly,

If you would have checked my original post what i meant to say was that even in copy and pasting we have a lot of problem.


you say open terminal and run this command.

but the problem comes when you suppose that user should have sufficient knowledge (ex he should navigate to perticular directory or so.) but the user doesn't have such knowledge, the case that i gave as an example is a live case.

i have lost that thread but i will give a link as soon as i find it.

My aim for posting is that 
answers should be given keeping in mind the user's level of experiance.

like 
for experianced user   :   decompress the package
for imtermediate / new cli user : tar xzvf <file_name>
for beginner : - right click on pakage and select extract here.

that thought just came in my mind coz i found this discrepency all over the forum, a problem which could have been solved by just 2 lines of command and / or just a few clicks takes a lot more than weeks to solve coz people are unable to explain properly.

PLUS we should have a proper syntax of telling the commands.

like i like to use <PATH TO PROGRAM> kind of syntax where as other 's might use /PATH/TO/PROGRAM.
So what i propose is that their should be a proper syntax that should be followed throughtout the forum. coz if i am corret most of the ubuntu users don't come from legacy users they are new in the field of linux.

ALSO as far as people getting to learn about linux is concerned.
if you just give them a command to do work they do a copy paste and forget about it. and when faced with simmilar probelm again reply on google to tell them a answer.



also a thought just came in my mind can't we have a facility like open "command promt here sort of " in nautilus (GNOME).
In KDE i can do that easily in konqueror by opening terminal emulator but how to do it in gnome coz UBUNTU is GNOME BASED. i might have missed it coz i rarely use GNOME.


I hope this would have cleared a lot of people's doubt.

---

### Post by popch on 2007-11-06
> **anantshri said:**
> i found this discrepency all over the forum, a problem which could have been solved by just 2 lines of command and / or just a few clicks takes a lot more than weeks to solve coz people are unable to explain properly.

PLUS we should have a proper syntax of telling the commands.

like i like to use <PATH TO PROGRAM> kind of syntax where as other 's might use /PATH/TO/PROGRAM.
So what i propose is that their should be a proper syntax that should be followed throughtout the forum. coz if i am corret most of the ubuntu users don't come from legacy users they are new in the field of linux.

You state your case as if the people here trying to help the beginners were under some sort of obligation, and the people wanting to use Linux were entirely free of the obligation to try and learn anything.

I think it is a very fine testimonials to the crowd here that they bother to help some helpless soul over a time of two weeks when a simple two line command would have fixed the problem, if only the helpless soul would have bothered to learn how to copy a command into a terminal window.


While you might be essentially correct in saying that there is need for a syntax for the use of a GUI, that syntax would be utterly useless for your purpose for the simple reason that the helpful users in this forum would know that syntax while the people seeking help would be put off by being told funny things in still - for them - funnier notation. I can already read the indignant protests about having to learn a syntax for using a GUI just in order to be able to use that geeky Linux stuff, and how much easier it all is in other products.

---

### Post by anantshri on 2007-11-06
> **popch said:**
> You state your case as if the people here trying to help the beginners were under some sort of obligation, and the people wanting to use Linux were entirely free of the obligation to try and learn anything.

I think it is a very fine testimonials to the crowd here that they bother to help some helpless soul over a time of two weeks when a simple two line command would have fixed the problem, if only the helpless soul would have bothered to learn how to copy a command into a terminal window.


While you might be essentially correct in saying that there is need for a syntax for the use of a GUI, that syntax would be utterly useless for your purpose for the simple reason that the helpful users in this forum would know that syntax while the people seeking help would be put off by being told funny things in still - for them - funnier notation. I can already read the indignant protests about having to learn a syntax for using a GUI just in order to be able to use that geeky Linux stuff, and how much easier it all is in other products.

The synax is for CLI and not GUI.

also having a uniform syntax throughout the forum will be better and we can keep a sticky at all threads regarding syntax,

and its nothing funny, its like you wished to read a book and you started with page 30 and found the book not readable coz they have highlighted sections you ought to know.

but in the other hand people as atleast this much educated so that they can work on to get an idea about new syntax.

and i am not talking about heavy syntaxing i am talking about little syntaxes spcially if you specify paths.

people find it hard why we should use hard or full paths (starting with / till the file) but for beginners this is the best method to understand the linux file system.

also I HIGHLY APPRECIATE THE EFFORT PUTTED BY HELPFUL PEOPLE BY TRYING TO KEEP HELPING THE PERSON,

but was this help of any use, when an example usage of full path could have avoided the hassels or by using ~ as home directory reference it could have been avoided all together.

AND THE SYNTAX should be thier to help poster get ease of posting and reader a nice understanding.

and if my post feels offending to any one then i am  sorry for him/ her but i don't mean to hurt them, but raise a point.

---

### Post by aysiu on 2007-11-06
Whether I give GUI instructions or CLI instructions greatly depends on the situation. I tend to favor CLI instructions, since... [list][*]this is a text-based forum[*]I have no idea usually what desktop environment people are using[*]the terminal commands will give useful (to me, anyway) error messages should they not work [*]I always, except in the case of recovery mode, encourage people to copy and paste commands instead of retyping them.[/list] In my time on these forums, however, I have also included 1,031 screenshot attachments to posts (and, no, not ones showing off my desktop). There are definitely situations that warrant a screenshot or two (for example, if someone says "I've lost my top panel. How do I get it back?").

It all depends on the situation.

But we are a text-based forum. People *can* copy and paste (I hope). And terminal commands are better for troubleshooting. I'd much rather have someone post an error message than say "Nothing happened" or "It just disappeared."

---

### Post by keyboardashtray on 2007-11-07
> **asjdfwejqrfjcvm msz34rq33 said:**
> A couple of reasons why the CLI (Command Line Interface) is better than the GUI (Graphical User Interface):
[LIST]
[*]It is much easier to say "Copy and Paste this" than to say "Click here, then click here, then right click here, then press this button..."
[*]It teaches the guy asking the question a little more about Linux, which is always good.[/LIST]

I'm sorry, but I see that second line spouted off as dogma all the time, that it "teaches more".

Where are the facts on that?

Just because it is *harder* and less intuitive to most people, doesn't inherently *teach them more* about anything.

The only thing it *might* teach them more about is the command line -and I even have doubts about that, when the general consensus seems to be "oh just copy and paste this and you'll be fine". And even if it does teach them more about the command line, it is at the expense of them learning the GUI method that I'm sure many would prefer if it exists in a scenario.

The whole reason personal computing as a whole is going to the GUI is that it provides contextual clues that help to both figure out how to do something and remember it.

As for the first point, I'll agree it is easier for those on the answering end. But I think many people drop sudo command advice at the drop of the hat with one side of their mouth while suggesting sudo caution with the other. I'm sure most would counter with "well, it's the responsibility of the recipient to learn what the given command does." And they'd be right. 

But then we come full circle to the GNU/Linux stereotype, which people say is false when it suits them (recruitment) and adhere to when it suits them (posts like this).

---

### Post by Nano Geek on 2007-11-07
> **keyboardashtray said:**
> I'm sorry, but I see that second line spouted off as dogma all the time, that it "teaches more".

Where are the facts on that?

Just because it is *harder* and less intuitive to most people, doesn't inherently *teach them more* about anything.

The only thing it *might* teach them more about is the command line -and I even have doubts about that, when the general consensus seems to be "oh just copy and paste this and you'll be fine". And even if it does teach them more about the command line, it is at the expense of them learning the GUI method that I'm sure many would prefer if it exists in a scenario.

The whole reason personal computing as a whole is going to the GUI is that it provides contextual clues that help to both figure out how to do something and remember it.

As for the first point, I'll agree it is easier for those on the answering end. But I think many people drop sudo command advice at the drop of the hat with one side of their mouth while suggesting sudo caution with the other. I'm sure most would counter with "well, it's the responsibility of the recipient to learn what the given command does." And they'd be right. 

But then we come full circle to the GNU/Linux stereotype, which people say is false when it suits them (recruitment) and adhere to when it suits them (posts like this).Well, anything that makes you do something "out of the norm" is a learning experience. I'm not saying that everyone will need to know how to use the command line, but, at least for me, it helps greatly to be able to use it to figure out why a program is not working or to be able to compile a new piece of software.

---

### Post by keyboardashtray on 2007-11-07
> **asjdfwejqrfjcvm msz34rq33 said:**
> Well, anything that makes you do something "out of the norm" is a learning experience. I'm not saying that everyone will need to know how to use the command line, but, at least for me, it helps greatly to be able to use it to figure out why a program is not working or to be able to compile a new piece of software.

While I understand the practical applications of knowing the command line (obviously I agree it is useful knowledge) what I take issue with is the implication, in the post I quoted and I suppose a little with the "out of the norm" part of your comment, is that the challenges perceived in the command line carry merit of their own, if only for the sake of being difficult. Then to take it further and use that false merit as weight against the practicality of GUIs when comparing the two. 

I agree that the CLI can do more, but I chalk that up to a weakness in a given GUI, not a strength of the command line. At least as far as the end user should be concerned.

---

### Post by Nano Geek on 2007-11-08
> **keyboardashtray said:**
> While I understand the practical applications of knowing the command line (obviously I agree it is useful knowledge) what I take issue with is the implication, in the post I quoted and I suppose a little with the "out of the norm" part of your comment, is that the challenges perceived in the command line carry merit of their own, if only for the sake of being difficult. Then to take it further and use that false merit as weight against the practicality of GUIs when comparing the two. 

I agree that the CLI can do more, but I chalk that up to a weakness in a given GUI, not a strength of the command line. At least as far as the end user should be concerned.I guess that it just boils down to personal preference. I personally find the command-line to be great for certain tasks, but some users might feel otherwise. 

As for giving command-line commands to new users asking for help, as I said before it is easier to say copy this in the command-line and everything should work than to say click here, click there, copy this in here, and right click on this and press OK. But again it's just personal preference.

---

### Post by keyboardashtray on 2007-11-08
> **asjdfwejqrfjcvm msz34rq33 said:**
> 
As for giving command-line commands to new users asking for help, as I said before it is easier to say copy this in the command-line and everything should work than to say click here, click there, copy this in here, and right click on this and press OK. But again it's just personal preference.

Yeah, I do agree, they even give you those cool little code boxes.

```
im in ur root  hackin ur xorg
```

---

### Post by anantshri on 2007-11-08
To keyboardashtray,

thanks buddy thanks for understanding my point.


> **asjdfwejqrfjcvm msz34rq33 said:**
> Well, anything that makes you do something "out of the norm" is a learning experience. I'm not saying that everyone will need to know how to use the command line, but, at least for me, it helps greatly to be able to use it to figure out why a program is not working or to be able to compile a new piece of software.

also its better for debugging purpose. but what about unzipping softwares or just running a application, or take a simple case of adding an apt key in the keyring, 

people always tell about a long method and that is to download the key first and then add the key using text mode, 

but how many how thought this approach, start synaptic, add your required reposatory, and then allow the update to happen, eventually it wll say that "X123YZ" key is not in the keyring, juist copy paste it in the gui apt key manager.

that would help the new breed to work more easily.

also i have been watching the post's they are mostly of the sort if you wish to work on GNU / Linux learn and learn and learn,

well i will now like to share my exp. i have been working on linux for the past 7 years, in the begining i didn't knew anything about commands , but i have worked all my stuff on linux through GUI only for 3 years, and after that when i moved to administration stuff, and that too server and all, i sometimes prefered CLI, stil today i give advice to start working on GUI and if possible avoid CLI.


IF people wanted everyone to use CLI why are a lot of talent working on GUI tools, webmin, winetools, wine-door, to name a few, why can't everyone let it be on CLI then.

my point is 
if possible then give them two options 
1) you can do this in GUI like this and if this doewn't works then move on to CLI and do this.

also most of the debug output is mainly required if you are working on a self compiled packages, and if a person is self compiling a package then he will definately be able to understand your words,

THE PEOPLE I AM TALKING ABOUT HERE IS THE NEW BREED, and please people we are not here to scare away the new commers, other wise i would not have been in this place if people have not helped me.

I APPRICIATE THE AFFORD THAT PEOPLE PUT IN HERE WHILE ANSWERING THE QUESTIONS BUT my point is why to create more confusion when it could be done in a simple manner.

what we can do is we can have a documentation expert prepare documents on some common task,

and also PLEASE IF I SAY GUI i am not denying use of CLI competely, but if we can avoid CLI then please do it for betterment of the masses.

I HOPE I AM NOT HURTING ANYONE.

AND PLEASE SHARE YOUR VIEWS, it not a war kind of situation i have putted my point and i want feed back.

---

### Post by crhylove on 2008-05-17
> **aysiu said:**
> It's 2006, and I'm not offering VNC-guided phone support. I'm doing online support with text. The command-line is perfect for that.

What's easier?

This? 

or this?  By the way, the second set of instructions would have to be modified heavily for Xubuntu and Kubuntu. The first set of instructions would work for all three.

If you have nothing constructive to say, why are you posting here? Does your smarmy remark help anyone get write permissions to an external hard drive? Can I ask you how many screenshot-heavy tutorials you've created lately?

I've actually done a fair number of VNC tech support sessions, and also created a number of tutorials.  Further, I can appreciate the elegance of the command line, and your general helpfulness.  I don't think there's any call to fly off the handle like that though, and further it certainly doesn't help towards building a "community" which has been voiced as being one of the goals of Ubuntu somewhere on here.

The average user does NOT want command line console controls.  This is clear given the lack of DOS in the world, and the success of Windows and Mac OS, and even of Linux in general.  If the tools to correct minor issues like this are so arcane and complicated across multiple distros:  Perhaps we should really just focus on ONE distro, and further, perhaps the tools should NOT be so arcane.  In fact your post indicates clearly to me that the tools should be much easier to access, something I've been suggesting since day 1.  Sorry for coming off smarmy, but I would like to see Ubuntu and Linux in general succeed, and the command line is not going to make that happen.  Unless of course this was 1982.

---

### Post by aysiu on 2008-05-17
When I do end up offering VNC-guided support, I will give mainly GUI-based instructions. This, however, is a text-based forum, and the terminal gets the job done regardless of environment (KDE, Gnome, Xfce, IceWM, Fluxbox, etc.) and gives useful-for-diagnosis error messages if something goes wrong.

There are many who would disagree with you about how helpful or unhelpful I have been to building the Ubuntu community.

I don't see how chastising people who are trying to help and then chastising them again two years later builds community, though. I was helping someone. I have been helping users for the past three years, and if you visit my Psychocats tutorial site, you will see that almost all tutorials are screenshot-based GUI tutorials.

When it comes to troubleshooting, though, the terminal cannot be beat.

---

### Post by cardinals_fan on 2008-05-17
Well, I'm real sorry.  I guess that I should stop helping people out, since they get so upset when I give them a simple command to cut and paste.  After all, it hardly matters that the problem is solved quickly and easily if it takes the horrific copying and pasting of text to get there.

---

### Post by schauerlich on 2008-05-17
Wow, it took almost 2 years for the OP to respond to the first post. That's got to be a record necromance.

---

### Post by barbedsaber on 2008-05-17
please don't feed the troll.

---

### Post by Victormd on 2008-05-17
> **EDavidBurg said:**
> Wow, it took almost 2 years for the OP to respond to the first post.
I was wondering the same thing

---

### Post by cardinals_fan on 2008-05-17
> **EDavidBurg said:**
> Wow, it took almost 2 years for the OP to respond to the first post. That's got to be a record necromance.
Wow!  I just noticed that.

---

### Post by vexorian on 2008-05-17
1. GUI := learn yourself.
2. CLI := remote assistence through copy paste.

When people look for help here, I would say they want #2.

---

### Post by p_quarles on 2008-05-18
> **crhylove said:**
> How about a way without command line?  Seriously.  What year is this?
2006.

> **crhylove said:**
> I've actually done a fair number of VNC tech support sessions, and also created a number of tutorials.  Further, I can appreciate the elegance of the command line, and your general helpfulness.  I don't think there's any call to fly off the handle like that though, and further it certainly doesn't help towards building a "community" which has been voiced as being one of the goals of Ubuntu somewhere on here.

The average user does NOT want command line console controls.  This is clear given the lack of DOS in the world, and the success of Windows and Mac OS, and even of Linux in general.  If the tools to correct minor issues like this are so arcane and complicated across multiple distros:  Perhaps we should really just focus on ONE distro, and further, perhaps the tools should NOT be so arcane.  In fact your post indicates clearly to me that the tools should be much easier to access, something I've been suggesting since day 1.  Sorry for coming off smarmy, but I would like to see Ubuntu and Linux in general succeed, and the command line is not going to make that happen.  Unless of course this was 1982.
Nope -- 2008. 

The average user, I'm guessing, doesn't want to have to have technical problems, much less have to fix them using any interface.

I'm closing this thread since it was started a very long time ago. Many threads beating this particular dead horse have been started and fizzled out since then.

---

