---
title: "How can I configure my keyboard so that accents work?"
date: 2024-07-25
forum: New to Ubuntu
---

### Post by whk102 on 2024-07-25
Hello, I have a keyboard full size 100% ansi layout ( [https://www.keyboard.university/100-courses/keyboard-sizes-layouts-gdeby](https://www.keyboard.university/100-courses/keyboard-sizes-layouts-gdeby) ), when installing Ubuntu 24.04 I have chosen the EN-us distribution, it works very well with all the keys set by the keyboard, even the secondary keys work very well for special actions such as volume control, but I have a problem:

Sometimes I have to create documents in Spanish and I need to use typical of an Es-es keyboard: ñáéíóú, at the moment I can add the distribution in Spanish in the Ubuntu administration panel and switch between keyboards every time I need it, but it is complicated when developing software, I am a developer and even though all the code is in English, the I have to make comments on it in Spanish and it is too uncomfortable for me to have to change the layout every time I need to create a comment. I also can't get used to constantly changing the position of the foreign key keys, parentheses and so on, when I need to. developing in Spanish I must be guessing where each key is and if I develop in the English distribution I must be copying the accented letters from other texts to paste into my code every time I need to write one.

To avoid this problem I have looked for a way to make the appearance of Latin characters coexist on my American keyboard with an American layout, I have found several alternatives but none of them work, at least not in Ubuntu 24.04 LTS, yes in 20.04 but from using wayland everything has become a bit complicated.

Xmodmap: It worked somewhat poorly but at least it worked a little in 22.04 but starting with Ubuntu 24.04 it has stopped working and is no longer an alternative, anyway every time I started the computer I had to run the xmpdmap command and still sometimes It stopped and did not apply to all users of the system, it was poor but it worked, it no longer works.

Native Gnome settings: There is an option in gnome settings to do key mapping with "Alternate character keys" and "Compose Keys" with left Alt, but enabling it does not activate the use of accents when pressing the combination plus the vowels. I have tried various layout configurations and enabling special settings from gnome settings without success. My idea is that pressing Alt Right + a or +Shift would write "á" or "Á", but ubuntu write "å" and Left+Alt is not found in options, only can see Right+Alt.

Xdotool: It was a very good option but unfortunately it only allows the execution of commands as an action, it does not allow the insertion of characters, I could have created my own combinations for each Latin character but I can't, I have tried to use xdotool to simulate the key but in Ubuntu 24.04 it is already it does not work. I try use ydotool but some keys don't work and it causes conflict with most applications and it doesn't even show me Latin characters well.

I would like it if with a combination of keys I could make the Latin letters appear, can someone help me please?

---

### Post by grahammechanical on 2024-07-25
Why not add an alternative keyboard layout. Then you can easily switch between layouts.

[https://help.ubuntu.com/stable/ubuntu-help/keyboard-layouts.html.en](https://help.ubuntu.com/stable/ubuntu-help/keyboard-layouts.html.en)

System Settings>Keyboard>Add input source>click the three vertical dots and scroll down the list. Select a layout. You should then get an icon in the top panel that will let you switch between layouts.

Regards


Regards

---

### Post by tea for one on 2024-07-25
> **whk102 said:**
> I would like it if with a combination of keys I could make the Latin letters appear, can someone help me please?
Using default gnome keyboard UK settings:-
Alt Gr semi-colon a		=	á 
Alt Gr shift underscore	=	¿

If these work with your US keyboard, I can add the complete list for Spanish

---

### Post by whk102 on 2024-07-26
@grahammechanical's  As I said in the previous post, my problem is when I have to write software code, while I write code I can't be changing layouts every time I need to write a code comment and go back to the previous one to continue programming, I would have to be changing layouts every minute, it's stressful.

---

### Post by whk102 on 2024-07-26
@tea for on thanks, works fine :)

---

### Post by tea for one on 2024-07-26
> **whk102 said:**
> @tea for on thanks, works fine :)
Splendid, here is the list

Alt Gr semi-colon a		=	á

Alt Gr semi-colon e		=	é

Alt Gr semi-colon i		=	í

Alt Gr semi-colon o		=	ó

Alt Gr semi-colon u		=	ú

Alt Gr [ u 			=	ü 

Alt Gr ] n			        =	ñ

Alt Gr = c			=	ç

Alt Gr semi-colon shift a	=	Á  

Alt Gr semi-colon shift e	=	É

Alt Gr semi-colon shift i	=	Í

Alt Gr semi-colon shift o	=	Ó 

Alt Gr semi-colon shift u	=	Ú 

Alt Gr [ shift u		        =	Ü 

Alt Gr ] shift n		        = 	Ñ 

Alt Gr = shift c		        =	Ç 

Alt Gr shift !			=	¡ 

Alt Gr shift underscore	=	¿

---

### Post by fabio.vcbrandao on 2024-12-06
I had a similar problem  as I have to write documents that mix Portuguese, English and sometimes French.
I added the english(US, intern., with dead keys) keyboard layout and it works except for some characters.
I can use all the accented vowels and ñ without any input changes. That should be enough for Spanish.

I'm still strugling with c-cedilla in this layout. Any ideas?

---

### Post by Irihapeti on 2024-12-06
Rather than try and find one layout that will do everything, you could use two (or even more) and switch back and forth between them using a keyboard command.

I sometimes work in English and M&#257;ori. I use a Latvian keyboard layout for M&#257;ori and switch to it only when I need it. My system is set up so that pressing left alt+left shift changes the layout.

---

