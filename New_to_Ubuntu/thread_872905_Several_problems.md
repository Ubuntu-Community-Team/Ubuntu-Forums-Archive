---
title: "Several problems"
date: 2008-07-28
forum: New to Ubuntu
---

### Post by LovelyAcorns on 2008-07-28
Okay, I'm new to using linux. I currently dont have internet, so I have to burn cds at friends' houses and then bring them home. Well, after doing that and following the whole makefile way of compiling the source codes, it always says that C compiler can't compile. What am I doing wrong? I was thinking maybe I needed the build-essential package or something? 

Also when I try to install things, it always ends up telling me I need to install some other package first, yet the website never seems to say that. How do you figure out what all the required packages are prior to an installation attempt?

Where am I supposed to store applications to be able to use them? Simply double clicking on the binary file does nothing.

Something went wrong with my keyboard setup, because the single and double quotes show up slanted, which python considers invalid syntax. I can't find my keyboard on the list, so I was wondering if there is another way?

Sorry for all the questions, but thanks if you can help me solve any of them.

---

### Post by Het Irv on 2008-07-28
I know that build-essential is on the Live CD, I am not sure where but if you boot into Ubuntu and stick in the Live CD is will prompt you to open a package manager.  I think you can install build essential from there.

The second problem may be related to the first or it might be that you are missing some dependencies for that program.  Which program are you trying to install?

There isn't any special place for programs, but to run binary files you may need to change the permissions, just right click on the file, go to properties, and then the permissions tab.  You should see a check box close to the bottom that when checked will allow you to run the file as a program.

What Keyboard do you have?

---

### Post by LovelyAcorns on 2008-07-28
> **Het Irv said:**
> I know that build-essential is on the Live CD, I am not sure where but if you boot into Ubuntu and stick in the Live CD is will prompt you to open a package manager.  I think you can install build essential from there.

The second problem may be related to the first or it might be that you are missing some dependencies for that program.  Which program are you trying to install?

There isn't any special place for programs, but to run binary files you may need to change the permissions, just right click on the file, go to properties, and then the permissions tab.  You should see a check box close to the bottom that when checked will allow you to run the file as a program.

What Keyboard do you have?



So the build-essential is the solution? And my ubuntu cd does not want to work with the package manager so I've given up on that. So I just burned it instead. And this serves as a perfect example for the second question, when I tried to install the build-essential it told me I needed a dbpkg or something file. Though I've figured this one out, apparently if I download from the ubuntu website it does show the dependent files at the bottom.

EDIT: Okay, I'm even more confised now, when I click on a dependent file I get another list of dependency files, and then another. It seems to download anything I need a huge hierarchy of packages. Is there some way to just download all dependent files at once? :/EDIT


Are you sure its just a permission thing? Because usually I get some kind of warning if I'm attempting to do something I don't have privilage to do. But absolutely nothing happens if I click on the file. And the files won't even have an icon, just that blue autorun square.

I don't have my keyboard model on hand, didnt think I was going to be able to get online today. I thought it was an eMachines keyboard, since it says eMachines on it, but ubuntu only lists laptop keyboards for eMachines.


And I hate to do this, but I just realized I forgot to add two questions. When I try to download things, it gives me choices of dapper or fiesty or gutsy. I'm not really sure which to pick. Also, some of the preinstalled games show up bigger than the screen and have no resize options. How do I fix that? Because it is a lot harder to win reversi when you can't access the bottom two rows.


Thanks for your help so far.

---

### Post by Het Irv on 2008-07-28
Easy ones first.  If you bought your computer in the United States, you more than likely have the default US layout.  A generic layout should work fine for you.  What are you using to write code, it may be the text editor "helping" you by converting your straight quotes.

Dapper, Feisty, Gutsy, and Hardy are all versions of Ubuntu.  The most recent one would be Hardy Heron 8.04.1.  Which one you want to download depends on what version of Ubuntu you have.

You should be able to use a file browser (nautilus) to browse the CD and find the packages and install them manually.  You should be able to double-click them once you find them and it will install the packages.

Permissions:  No I am not sure, but its worth a check.  And by permissions I don't mean user permissions, I meant file permissions. Close but not the same thing.

If you have any errors installing files can you paste them here, that would help alot.

---

### Post by LovelyAcorns on 2008-07-28
The slanted quotes happen in the Terminal, in OpenOffice's word program, and whatever the unbuntu's version of notepad is. So I don't think its all the applications causing it. What would be a good choice for a generic keyboard layout that I should chose?


And the thing is, I'm not sure how to get all the required packages to a cd in the first place. When on ubuntu's website's package section, an application I want will have between 5 and 10 files its dependent on. And then each of those dependencies has between 5 and 10 files its dependent on. And so on. And there are several overlaps where different packages all are dependent on another package. There has to be some way to get all the required packages that doesn't require me to make a spreadsheet every time I want to install something. I must be doing something wrong.


EDIT: I have to leave and won't be on for a few days, so sorry that I won't respond right away.

---

### Post by Het Irv on 2008-07-28
It might help if you have can give an example of a program you are trying to install, so I can look at what you are trying to do, there might be an easier way to install the program than how you are doing it.

As for the Keboard,  I don't know because I haven't tried to code,  but I will ask around.

---

### Post by LovelyAcorns on 2008-08-03
Okay, I got the ubuntu cd to work, so I got build-essential. Now I can compile, though something or another goes wrong whenever I try to make something. I'm kind of giving up trying until I get internet. But, as an example, I'm trying to install apache and php. I've managed to actually make apache now, but I get error after error. And for Blender I changed the permissions, but it still wouldn't work.

On the keyboard note, when I was at the bookstore I glanced at a book on ubuntu. I noticed something about how there is some code you can enter for switching what a key prints. I can't remember the code though.

I'm still trying to figure out how to resize programs that don't have an option for doing so.

---

### Post by Het Irv on 2008-08-04
For all of your programs, why not download the .deb files from packages.ubuntu.com?  .debs are the perfered way of installing programs in Ubuntu, because it will automatically update the programs when updates are released.  You also don't have to worry about compiling and all that.

If you do want to compile your programs, what errors are you getting?

---

