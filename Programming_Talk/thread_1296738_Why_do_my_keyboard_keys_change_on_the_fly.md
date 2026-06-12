---
title: "Why do my keyboard keys change on the fly"
date: 2009-10-21
forum: Programming Talk
---

### Post by mocatz187 on 2009-10-21
I typed a simple C program to try and get the hang of a linux prompt, so I typed the hello world program. after a successful compile and run, I went to add more code but my quotation marks have turned into tiny pairs of dots. this has affected everything that I type in. I am using US keyboard and it worked fine until I compiled and ran hello world. """""""""""""" these are from my windows computer.I'll try and login with the notebook with linux and display the wierd qoutes I'm getting there.

---

### Post by mocatz187 on 2009-10-21
This what I´ve got now ¨¨¨¨¨¨¨¨¨¨¨¨¨¨¨¨¨¨¨¨¨¨¨¨¨¨¨¨¨on Kubuntu. 
Anyone have any Ideas? Thanks.

---

### Post by mocatz187 on 2009-10-21
I have to hold shift down then press qout to get it to print to screen then if I  press the space bar down it prints a standard qoute, but only once - it then continues to work as space.

---

### Post by Tony Flury on 2009-10-21
Have you checked that you have the correct Keyboard set up - System -> Preferences -> Keyboard.

There should be no reason why a Hello world program should impact your keys or keyboard - can you post the code of your program, it might be that your code has a side-effect. Use the CODE tags when you include your source code.

---

### Post by mocatz187 on 2009-10-21
Yes keyboard is correct.
this is the code:
 
#include <stdio.h>
int main () {
 
printf ("hello world");
 
return 0;
}

---

### Post by mocatz187 on 2009-10-21
Then in command line:
gcc -Wall -o hello hello.c
 
I was in the appropriate directory.
When I removed the offending quotes in the new code the compiler and shell were happy.
But now it does something weird, it requires you to hit the key twice to get one output and if you hit it once and then hit the space bar it will make a qoute that is code compatable. 
it's almost as if I somehow toggled some sort of letter highlighter or punctuator or ???

---

### Post by Tony Flury on 2009-10-21
I can't see that the code that you have given would cause any changes to your keyboard or key mappings.

Does it still do the keyboard funny over a reboot ?

It might be (long shot) that your keyboard is mis configure, you might need to reset the config (delete the layout definition and start again).

ANother suggestion is to post your question in General help, as I am fairly sure the problem is not connected with your little "Hello World" app.

---

### Post by mocatz187 on 2009-10-21
I set keyboard to us generic but no change. I have run DSL Linux as a live CD and did not have any issues.
Looks like I'm gonna have to  remove this OS!

---

### Post by mocatz187 on 2009-10-21
Yes I'm going to post this thread in general help.
I will keep this one open for 24 hours to see if I get any responses.
thanks.

---

### Post by mocatz187 on 2009-10-21
Wow, I'm really surprised that nobody has been able to help..
I guess there is no fix and the best option is to search for linux distros that don't support dead keys or accented letters.
I mean, I've got an excuse, I used windows vista prior to this and XP before that   it's perfectly excusable that I don't know how to turn this off but whats your excuse (the ubuntu kubuntu community).

---

### Post by Can+~ on 2009-10-21
Could you describe the exact steps? Maybe someone will be able to reproduce it.

---

### Post by wmcbrine on 2009-10-21
> **mocatz187 said:**
> I guess there is no fix and the best option is to search for linux distros that don't support dead keys or accented letters.No such thing.

> *I mean, I've got an excuse, I used windows vista prior to this and XP before that it's perfectly excusable that I don't know how to turn this off but whats your excuse (the ubuntu kubuntu community).*That we've never needed to. Either we actually want the behavior, or we've never run into it.

IIRC, the behavior you describe is what I saw with a U.S. International layout. I don't get it with a regular U.S. layout. I've never gotten it as the default setup; I had to explicitly select it, when I wanted to test support for dead keys etc. in a library I was maintaining (PDCurses).

Looking at the Gnome keyboard option widget now, it seems to have changed a lot since I last used it. I find to my surprise that my current layout is shown as "(Intl)", though I don't have dead keys. I know there's a way to switch, but I can't say offhand what it is.

Try Googling on "Ubuntu dead keys", etc.

---

### Post by mocatz187 on 2009-10-22
Kubuntu seems to be like some sort of b@st@rd stepchild to ubuntu.the documentation is sparce for Kubuntu and different than the GNOME environment on Ubuntu. I don't even know why I chose Kubuntu over Ubuntu really? I'm pretty disgusted with it.I read a little here [https://help.ubuntu.com/community/ComposeKeybut](https://help.ubuntu.com/community/ComposeKeybut) I don't have Ubuntu, I have Kubuntu.They always mention Ubuntu and Xubuntu but rarely is Kubuntu mentioned. The closest thing thing you ever hear about Kubuntu is that the documentation should work on other versions.If Kubuntu is being described as "other versions" in the documentation I think that that should have sent red flags off in my head. There are a lot of bugs reported on the net about international characters  and the associated patches in Kubuntu, why Kubuntu & not others, I guess we'll never know.I guess when I have some time I'll check that box they write about at the documentation page for Ubuntu, just to see if that fixed it but I should probably be using Ubuntu over Kubuntu if I want to be able to sort this kind of stuff out. I can only imagine how many people reading these forums ignore certain posts because it has an Kubuntu prefix instead of Ubuntu.

---

### Post by mocatz187 on 2009-10-22
Yeah I googled dead keys Kubuntu and found info about Ubuntu only.I have been through every keyboasrd setting. You have to look under languages and regional or something like that.And it seems that Ubuntu an Xubuntu both have relatively easy fixes but Kubuntu is completely different.If they won't wright documentation for one of the versions they should just end it.Thats the solution to this problem, get rid of Kubuntu!Stick with the mainstream and download Ubuntu.

---

