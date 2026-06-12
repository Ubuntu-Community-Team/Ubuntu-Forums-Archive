---
title: "How to open my .bash_profile. beginner question. Please please help xP"
date: 2011-03-16
forum: Programming Talk
---

### Post by btf18 on 2011-03-16
[FONT=Verdana][SIZE=2]Hi, i have posted this in general help 2 days ago but didnt get much luck. Im doing a tutorial on shell scripting, and to continue with my tutorial i need to be able to open my .bash_profile, and add this line to the end of the file: [/SIZE][/FONT][FONT=Verdana][SIZE=2]export PATH=$PATH:/home/bin

Please help, Ive been awaiting an answer on general help but the advice isn't telling me how to do it, they are vague, and they are telling me how to get the same result in a different way, but from their advice i still dont even know how to open my .bash_profile.

I use the text editor vim, so if you could tell me how to do it in that specifically that would be great, and explain it to me as though im a noob, maybe tell me exactly what to do. Thanks. I cant learn anything untill i can do this.
[/SIZE]
[/FONT]

---

### Post by wojox on 2011-03-16
So you want to add a /bin directory from home to $PATH this is what I do.

Open your Home Directory and press Ctrl+H

Look for .bashrc and add this to the very bottom

```
if [ -d ~/bin ] ; then
    PATH=~/bin:"${PATH}"
fi
```

Make sure you have already created that directory. Then run

```
echo $PATH
```

---

### Post by btf18 on 2011-03-16
Thanks so much. Im finally in the .bash_profile, however i dont understand the code. Its almost like the .bash_profile is using another language to what i've seen in the terminal and its confusing me. Do you have any tips to understanding this code so i can add commands in the future? Could you tell me what if and fi mean? also, what does [ctrl + H] technically do, when in home directory? I see it changed the folders showing

Ahh also, it didnt work :-( echo $PATH does not show /home/bin. Did i need to add a # or something? I just pressed enter on the .bash_profile to get one clear line below the last line, which was fi, then copied and pasted your code, then went file > save in the file menu.

---

### Post by wojox on 2011-03-16
if is an if statement. fi closes it out. It's used to test for a condition. You will learn more about that as you get more into scripting/programming

Ctrl+H shows hidden files. Everything that starts with a period (.)

You want to put that code in **.bashrc**

GUI terminals in Ubuntu are not login shells, so .bash_profile will not be run.

Log out and back in.

---

### Post by CharlesA on 2011-03-16
.bashrc already has that if statement in it, at least in Lucid.

---

### Post by btf18 on 2011-03-17
Thanks. I apologise, i did put it in .bashrc. I meant to type that. Hmm no worky xP

---

### Post by wojox on 2011-03-17
> **btf18 said:**
> Thanks. I apologise, i did put it in .bashrc. I meant to type that. Hmm no worky xP

And you created a folder named **bin** in your /home/btf18/ directory?

Logged out and in?

---

### Post by btf18 on 2011-03-17
no bin isnt in my /home/ben/ directory. Its in /home

IE if i typed ls in /home it would list ben, and bin

I did log out and in. The issue is with the directory name isnt it?

---

### Post by btf18 on 2011-03-17
I changed it to 
if [ -d /home/bin ] ; then
    PATH=/home/bin:"${PATH}"
fi

success! thanks so much. Could you tell me how to do the code box properly in these replies? haha

---

### Post by wojox on 2011-03-17
> **btf18 said:**
> I changed it to 
if [ -d /home/bin ] ; then
    PATH=/home/bin:"${PATH}"
fi

success! thanks so much. Could you tell me how to do the code box properly in these replies? haha

Cool. :P

For code tags press the # sign.

---

### Post by btf18 on 2011-03-17
I take it that code means if there is a -d (directory) /home/bin then PATH=/home/bin as in make it a path kinda thing. i guess its not toooooooo hard to understand
```

#/home/ben

/home/ben# just testing the code box

Thanks
```

---

### Post by wojox on 2011-03-17
> **btf18 said:**
> I take it that code means if there is a -d (directory) /home/bin then PATH=/home/bin as in make it a path kinda thing. i guess its not toooooooo hard to understand

Yes it adds it to your path. $HOME/bin or ~/bin or /home/username/bin

---

### Post by wojox on 2011-03-17
> **btf18 said:**
> I take it that code means if there is a -d (directory) /home/bin then PATH=/home/bin as in make it a path kinda thing. i guess its not toooooooo hard to understand

#/home/ben

/home/ben# just testing the code box but i dont think i have got it down xP

Thanks

Look up top at the tools and look for the # sign. 

EDIT: We have a Winner.

---

### Post by btf18 on 2011-03-17
yes all those directories are wrong for my directory though as its /home/bin not /home/ben/bin. Thanks a bunch. Haha yeah i quickly realised and edited out the text saying i couldnt get it down but you caught me xP

---

