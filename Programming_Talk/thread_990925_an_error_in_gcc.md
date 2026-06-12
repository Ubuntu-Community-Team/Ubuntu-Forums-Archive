---
title: "an error in gcc"
date: 2008-11-23
forum: Programming Talk
---

### Post by phanipalagummi on 2008-11-23
i m quite experience in c(xp),but very new to linux

my doubt is in gcc-compilation

I have a hello.c file stored on desktop

and when i do this
gcc -o hello hello.c
i m getting the following error
hello.c: No such file or directory
gcc: no input files

please suggest me something i m really getting stuck

---

### Post by geirha on 2008-11-23
When you open a terminal, you'll be located in your home-folder (/home/*username*), your desktop is located inside that, usually /home/*username*/Desktop, though it may be localized. Run
```
xdg-user-dir DESKTOP
``` to see the path to your desktop, then ```
cd Desktop
``` to enter Desktop (if it was called that). Run the ls command and confirm that hello.c is there, then run your gcc command.

---

### Post by phanipalagummi on 2008-11-23
again i m getting the same error

---

### Post by geirha on 2008-11-23
You are certain hello.c is located on your desktop, and you got uppercase and lowercase right? There's a difference between hello.c and Hello.c in linux. Try this command to search your home-folder for your .c-file.

```
find ~ -iname "hello.c"
```

---

### Post by phanipalagummi on 2008-11-23
yes i m certain that hello.c is on my Desktop

moreover when i tried that(find ~ -iname "hello.c") code it said nothing.(no error or exception too)

---

### Post by geirha on 2008-11-23
Hm, that means it didn't find any files named hello.c anywhere under your homedir. Try widening the search to any .c-files
```
find ~ -iname "*.c"
```

---

### Post by phanipalagummi on 2008-11-23
it gave this

/home/dheera/NetBeansProjects/mygodsname/newfile.c
/home/dheera/.netbeans/6.0/config/Templates/cFiles/newfile.c
/home/dheera/Desktop/hello.c
/home/dheera/Desktop/name.c

---

### Post by geirha on 2008-11-23
That's weird, the first find should've found the /home/dheera/Desktop/hello.c 

This really should work.
```
cd /home/dheera/Desktop/
gcc -o hello hello.c

```

---

### Post by phanipalagummi on 2008-11-23
lott thanks to you 

it's working

by the by there is no conio.h<header file>

how tosee all header files and associated functions in it(with little description of function)


please give some material also

---

### Post by jimi_hendrix on 2008-11-23
we use ncurses.h i believe...conio.h is used to interface with DOS...since linux doesnt use DOS conio.h wont work

---

### Post by slei3 on 2008-11-23
most people aren't sure of what they really want in life. I received this letter from a friend on the computer, did what it told me to, and within a week, everything I had wished came true!! Here's an exact copy,

this

really

works!!!!











*************************************************************







1. To yourself, say the name of the only guy or girl you wanna be with 3 times!











*************************************************************











2. Think of something you wanna accomplish within the next week and say it to your self 6 times!!











&#126;&#126;&#126;&#126;&#126;&#126;&#126;&#126;&#126;&#126;&#126;&#126;&#126;&#126;&#126;&#126;&#126;&#126;&#126;&#126;&#126;&#126;&#126;&#126;&#126;&#126;&#126;&#126;&#126;&#126;&#126;&#126;&#126;&#126;&#126;&#126;&#126;&#126;&#126;&#126;&#126;































3. If you had 1 wish what would it be? say it to yourself 9 times!!!








-----------------------------------------------------------------------















4. Think of something that you want to happen between you and that 1special person and say it to your self 12 times!!!












--------------------------------------------------------------------















5. Now, heres the hard part! Pick only 1 of these wishes and as you scroll down focus and concentrate on it and think on nothing else but that wish.











* *



* *



* *



* *



* *



* *



* *



* *



* *



* *



*

*



* *



* *



* *



* *



* *



* *



* *



* *



* *



* *



* *



* *



* *



* *



* *



* *



* *



* *



* *



* *



* *



* *



* *



* *



* *







Now make one last &amp; final wish about that one wish that you picked.







After reading this, you have 1 hour to send it out to 15 people, and what you wished for will come true within in one week!







u only get one chance!!!!! Now scroll down and think of your
crush!!!



























































Keep going

down



























Keep going







































Keep

going








































!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!











Did you think of your crush? I hope so, that was your last chance. Now pay very close attention this important message!



Sorry but once read, must be sent. Yes, this is one of those kinda chain letters that everyone hates. This one has been going since 1864 and if you break this chain, you will pay!!!!!! Remember that after hearing these stories.







First Example:



Take Barbra Wallace.. She was a pretty lucky girl, up till she got this same chain letter. She had a crush on the same kid since kindergarden. when she got this mail she didn't pay any attention to it. She just thought, no big deal. And deleted it. The next day her dad got fired and her mom dies in a car crash. If she would have sent the letter none of that would have happened and her mom would be alive.







Second Example:



Try Freddie D. Now Freddie D. was your average nerd. Had glasses, was short and chubby, was in gifted. All the signs of
your total dork. He also received this letter and sent it to 51
people in the hour. Now, like Barbra, he had a crush on a girl since 3rd grade. The next day after sending the chain the girl confessed her love for him ever since 3rd grade. Freddie D. finally had the courage to ask her out, and of course, she had been waiting to yes to that for years. They grew up and
married each other to live happily forever.







Third Example:



Now if you couldn't relate to the others, this'll get ya hooked. Listen to this. A kid named Jordan Johnson was just getting on AOL to check his mail. He was a quiet kid, not that popular but not a geek either. he was just normal. He saw he had mail from his friend. It was this exact letter. Now Jordan Johnsen was a smart kid and he knew what could happen if he didnt pass it on. He simply pulled a few friends from his buddy list and sent it along. The next day, about that same time, he got a phone call. It said he had won the lottery!
then his dad came home and bought him a new bike! His mom bought him Nintendo64 and play station! His grandmother sent him a new computer, and his best friend
gave him tickets to the concert he wanted to go to, Kid Rock and Limp Bizkit! Then he inherited a brand-new tv from his aunt! He was goin' wild! the next day his secret crush asked him out, and they have been going out ever since.







Now, you heard the stories. I know which person i'd rather
be, but thats up to you. I wouldn't wanna end up like Barbra but thats only me. We all want what we cant have but now's ur chance to go out withthat special somebody ur waiting for. Take it or leave it. If you send this to-



1 person- you will lose all luck in ur love life..... forever!!!!!



10 people- your crush will say they like you as a friend...... ONLY!!!!!



15 people- your crush will say they like you



20 people- your crush will ask you out!



25 people- your crush will kiss you!!




35 people or more- All of the above!!



Don't blow it, it's ur chance to shine! Have everything u wanted, and more! Now, complaining cus u dont have any
friends. Well theres an answer 4 everything. It's simple, just go in a chat room, pick some names and send away! but here's the catch..... you only have 1 hourtoReply to &quot;Re: &quot;&#171; back to messageto: &amp;hearts;lisa loves jt always &amp; 4ever&amp;hearts;

[change]
subject:
message: [color] Dark Red Red Orange Brown Yellow Green Olive Cyan Blue Dark Blue Indigo Violet White Black [size] Tiny Small Normal Large Huge
hey that chain message does it really work. and if it does that is awsome

Please wait...




Exclusive Features
See all

Freewebs Help TipsStart your Own Mailing List

Want to keep friends, family, customers and more in the loop about the latest on your site?

You can send event invites, monthly newsletters, product updates and more!

Create a Site Mailing List

---

### Post by geirha on 2008-11-23
Indeed ncurses is what you use instead of conio in linux. To get started, install [apt://libncurses5-dev](apt://libncurses5-dev), then open file:///usr/share/doc/libncurses5-dev/ in a browser for howtos and examples.

---

### Post by cmay on 2008-11-23
also make sure you have the build.essential package installed.
 most errors like "gcc no input files" are due to missing the build-essential package.

---

