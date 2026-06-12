---
title: "How to make this trick to type accents work?"
date: 2014-02-10
forum: New to Ubuntu
---

### Post by Oinos on 2014-02-10
Hi there. I just moved to ubuntu 13.10 and am completely new to everything linux.

Now I figured out the compose key stuff. The thing is, I find many of the sequences unintuitive to me ( ;a gives &#261; and not ä, you have to type the diacritic first and then the letter and not vice versa, etc.), and many I need are missing, e.g. &#8594;, &#8709;, &#658;, &#619; and so on.

Using the search I found something that seems promising:

> **Buck2348 said:**
> This is a helpful post, Jem7v.  I stumbled onto  the compose key a few weeks ago, probably while reading the Forums.  One  of the best features of Linux is that almost anything you do with it  can be customized.  Same for using the Compose Key.  For some reason  Edgy isn't set up as well as it might be for using it.  For example, you  can't make fractions like ½ with it.  To fix that you need to add a  line to /etc/environment:
```
gksudo gedit /etc/environment
```
add the following:
```
export GTK_IM_MODULE=xim
```
now copy a file to your home folder:
```
cp /usr/share/X11/locale/en_US.UTF-8/Compose ~/.XCompose
```
This will give you a more complete character set.  Also you can edit  that file.  Suppose for example that your keyboard doesn't have a tilde  (~).  You can change the lines that require entering a tilde so that a  simple "t" (or whatever you like) wil work.  Just don't use a key  combination that's already in use somewhere else.  You can check that by  entering the combination before you change anything and see if you get  any character output.  Also you can browse through this file to find the  key combination for the character you want if it isn't fairly obvious.

I learned this from this thread:  [http://ubuntuforums.org/showthread.php?t=209115](http://ubuntuforums.org/showthread.php?t=209115)

Buck

The thing is, as a completely new to ubuntu, I don't know how or where to execute that code. Do I need to run it in the console? Do I need to go to those directories first? Do I need only to edit some files? Also, will this work ubuntu 13.10?
And can it handle sequences of more than two keys - such as <n a u g h t> to give &#8709;?

And since there's [such](http://ubuntuforums.org/announcement.php?f=326) announcement, could you tell me, the newbie, if the code is perfectly safe.

Thanks in advance.

---

### Post by ajgreeny on 2014-02-10
That code should be run in terminal from your home, and there is no need to go to the specific folders as full pathways are shown, eg ```
cp /usr/share/X11/locale/en_US.UTF-8/Compose ~/.XCompose
```simply copies a file **/usr/share/X11/locale/en_US.UTF-8/Compose** from the system to your home.

As to the safety of those commands, I have no real info on that, nor what they might do to help your problem, but I can see nothing in them that gives me cause for concern, and it would be easy to reverse these actions if they cause problems.

---

### Post by Oinos on 2014-02-11
I typed in the commands in what appeared to be a console (got that after presing alt when in main screen), but apparently nothing happened. :(
Then I tried changing the file itself, which seems is all what i need, but an error was thrown that I dont have the permissions to. How can I acquire them?

---

### Post by Impavidus on 2014-02-11
On a default Ubuntu you can open the terminal with ctrl+alt+t (if I'm correct, I don't use a default Ubuntu myself). Else open the dash and search for "terminal", or find a menu with "terminal" somewhere or it could be in the dock on the left. It should give you a window with a line of text like **user@machine:~$**.

Then give the command **gksudo gedit /etc/environment**. It will ask for your password and open a file for you, with root permissions. Those are the permissions you need. Add the abovementioned line to the file, save the file and exit the text editor.

Back in the terminal, give the command **cp /usr/share/X11/locale/en_US.UTF-8/Compose ~/.XCompose**. If you don't use the en_US.UTF-8 locale, you may have to replace that part, but I found that the Compose files of many other locales here are just symbolic link to the one for the en_US locale, so that wouldn't matter. This will then create the file **.XCompose** in your home directory (/home/your-user-name/.XCompose). This file contains the definitions for your compose key sequences. You can modify them and save the file. Log out and log back in to apply the changes.

You can make sequences longer than two keys and will find many of them predefined, but you cannot make a sequence of which the first part already forms a different sequence. For example, if **compose o '** already gives ó, you cannot use **compose o ' '** to create &#337; (for which, by default, **compose = o** is used).

I use the compose key all the time, but I never had a need to modify the sequences, so I never tried this method. I think however that it should work and at least not do any damage.

---

### Post by Oinos on 2014-02-15
Thank you for the help. However I'm having problems with making it work. At best, when I enter the combination, nothing happens, but more often it just enters the second letter of it, e.g. if it is 
<Multi_key> <a> <e> : "i" whatever #my own combination 
it just enters 'e'. I tried this both with the original file and the new .XCompose

---

### Post by Oinos on 2014-02-16
Never mind, it works, it's just that I didn't notice or something. However, there are two issues:
1) Somewhere along the way, this functionality got lost:
> Another means to enter non-keycap characters is to enter them as Unicode character number. 
Press **Shift**+**Ctrl**+**U**, release **U**, enter the hexadecimal (0123456789abcdef) Unicode character code point, then release **Shift**+**Ctrl**. An underlined u followed by the number will be displayed as you type. 
Alternatively, press (and release) **Shift+Ctrl+U**, then, while underlined u is displayed, enter the hexadecimal Unicode character code point followed by <Return>.
Do you know how to restore it?

2) The compose sequences don't accept any cyrillic symbols. Why so? Is there any workaround? Or is it that it works with physical keys rather than with unicode symbols as input?

---

