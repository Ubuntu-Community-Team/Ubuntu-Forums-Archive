---
title: "On the Subject of Building a Distribution"
date: 2006-07-23
forum: Other OS Talk
---

### Post by Iandefor on 2006-07-23
I love baroque titles :).

I've been looking about for a tool to help me build my own Linux. I've collected a few options and thought I'd share them :).

I. [Linux From Scratch]("http://www.linuxfromscratch.org/")
II. [MkDistro (In Portugese?)]("http://www.dreamlinux.com.br/english/saiba-tutor.html")
III. [ROCK Linux]("http://www.rocklinux.org/wiki/Main_Page")
IV. [Ubuntu Customization Kit]("http://lichota.net/%7Ekrzysiek/projects/ubuntu-livecd-customization/")
V. [Kadischi (Requires Fedora Core)]("http://fedoraproject.org/wiki/Kadischi")
VI. [Livecdanaconda (Requires Fedora Core)]("http://www.linux4all.de/livecd/livecdanaconda/index.htm")
VII. [Morphing-Morphix]("http://www.morphix.org/index.php?option=com_content&task=view&id=64&Itemid=59")
VIII. [Debian From Scratch]("http://www.debian-administration.org/articles/125")
IX. [Reconstructor]("http://reconstructor.aperantis.com/")

That's all for now. Enjoy!

---

### Post by RAV TUX on 2006-07-23
> **Iandefor said:**
> I love baroque titles :).

I've been looking about for a tool to help me build my own Linux. I've collected a few options and thought I'd share them :).

I. [Linux From Scratch]("http://www.linuxfromscratch.org/")
II. [MkDistro (In Portugese?)]("http://www.dreamlinux.com.br/english/saiba-tutor.html")
III. [ROCK Linux]("http://www.rocklinux.org/wiki/Main_Page")
IV. [Ubuntu Customization Kit]("http://lichota.net/%7Ekrzysiek/projects/ubuntu-livecd-customization/")
V. [Kadischi (Requires Fedora Core)]("http://fedoraproject.org/wiki/Kadischi")
VI. [Livecdanaconda (Requires Fedora Core)]("http://www.linux4all.de/livecd/livecdanaconda/index.htm")

That's all for now. Enjoy!

I also have been interested in this, also.

The MKDistro tool by Dreamlinux does seem like the best option to me.

The Dreamlinux devs have offered to help me build my own distro using the MKDistro tool, with all steps posted in the English language section of the forum.

last I looked I was looking for a reply back to my post, after I accepted their offer.

I would like to build a distro based on Ubuntu using Gnome with a Knoppix based hard drive detection.

Mepis is close to these specs but have based their release in KDE.

After trying Mepis I wasn't happy thus far with the sporadic stability, but I will continue to play with it.

I am very impressed with what has been coming out of Brazil:
1. Dreamlinux
2. Goblinux

---

### Post by RAV TUX on 2006-07-23
Still no response from Dreamlinux, I know they are highly busy with other projects but I PM'd the dev.

I offered to post a mirror thread here so they could:

1. get more exposer
2. hopefully draw more developers to them

refer to the Dreamlinux thread here:

[http://www.dreamlinux.com.br/phpBB2/viewtopic.php?p=1917#1917](http://www.dreamlinux.com.br/phpBB2/viewtopic.php?p=1917#1917)

---

### Post by Iandefor on 2006-07-23
Hell, if I could get an English-language translation of the BASH comments in MkDistro, I'd probably know all I needed to make it work.

---

### Post by RAV TUX on 2006-07-23
> **Iandefor said:**
> Hell, if I could get an English-language translation of the BASH comments in MkDistro, I'd probably know all I needed to make it work.

silly question...

did you try copy and pasting the text in an online translator?

babel? or other?

---

### Post by RAV TUX on 2006-07-23
> **Iandefor said:**
> I love baroque titles :).

I've been looking about for a tool to help me build my own Linux. I've collected a few options and thought I'd share them :).

I. [Linux From Scratch]("http://www.linuxfromscratch.org/")
II. [MkDistro (In Portugese?)]("http://www.dreamlinux.com.br/english/saiba-tutor.html")
III. [ROCK Linux]("http://www.rocklinux.org/wiki/Main_Page")
IV. [Ubuntu Customization Kit]("http://lichota.net/%7Ekrzysiek/projects/ubuntu-livecd-customization/")
V. [Kadischi (Requires Fedora Core)]("http://fedoraproject.org/wiki/Kadischi")
VI. [Livecdanaconda (Requires Fedora Core)]("http://www.linux4all.de/livecd/livecdanaconda/index.htm")

That's all for now. Enjoy!


another option you could use that the Dreamlinux people used is Morphix:

Morphing-Morphix

[http://www.morphix.org/index.php?option=com_content&task=view&id=64&Itemid=59](http://www.morphix.org/index.php?option=com_content&task=view&id=64&Itemid=59)

---

### Post by Iandefor on 2006-07-23
> **yozef said:**
> silly question...

did you try copy and pasting the text in an online translator?

babel? or other? hmm.. I don't usually think of those in a serious manner. Usually, I have fun babelizing things, but I suppose I could use it to get the gist of what was being said.

---

### Post by Iandefor on 2006-07-23
Okay, so I'm starting the process of roughly translating MkDistro from Portuguese to English. It's not as hard as I thought it would be. I look at the code, get an idea of what something is supposed to do, double-check by seeing if there are any cognates between the Portuguese and English or Spanish  (IE, ver pacotes instalado), and, if all else fails, I run it through Babelfish to get a rough idea of what it means.

EDIT: There's one phrase that keeps recurring:

"gerenciador de janelas" and it stumps Babelfish and FreeDict. Anyone know what it means?

---

### Post by RAV TUX on 2006-07-23
> **Iandefor said:**
> Okay, so I'm starting the process of roughly translating MkDistro from Portuguese to English. It's not as hard as I thought it would be. I look at the code, get an idea of what something is supposed to do, double-check by seeing if there are any cognates between the Portuguese and English or Spanish  (IE, ver pacotes instalado), and, if all else fails, I run it through Babelfish to get a rough idea of what it means.

EDIT: There's one phrase that keeps recurring:

"gerenciador de janelas" and it stumps Babelfish and FreeDict. Anyone know what it means?

"manager of windows"

I used [Free **Translation**.]("http://www.freetranslation.com/")[]("http://ets.freetranslation.com/")

---

### Post by Iandefor on 2006-07-23
> **yozef said:**
> "manager of windows"

I used [Free **Translation**.]("http://www.freetranslation.com/") thanks. So it means Window Manager...:-k

---

### Post by RAV TUX on 2006-07-23
> **Iandefor said:**
> thanks. So it means Window Manager...:-k

  basically:p

---

### Post by leech on 2006-07-24
I think you forgot one, called dfsbuild, it's in the Debian and Ubuntu repositories already, and it's the one in which Debian uses to make ISOs.

Thought of trying it myself...dfsbuild is the Debian From Scratch project.

Leech

---

### Post by Iandefor on 2006-07-24
> **leech said:**
> I think you forgot one, called dfsbuild, it's in the Debian and Ubuntu repositories already, and it's the one in which Debian uses to make ISOs.

Thought of trying it myself...dfsbuild is the Debian From Scratch project.

Leech Added it.

---

### Post by RAV TUX on 2006-07-25
> **Iandefor said:**
> Okay, so I'm starting the process of roughly translating MkDistro from Portuguese to English. It's not as hard as I thought it would be. I look at the code, get an idea of what something is supposed to do, double-check by seeing if there are any cognates between the Portuguese and English or Spanish  (IE, ver pacotes instalado), and, if all else fails, I run it through Babelfish to get a rough idea of what it means.

EDIT: There's one phrase that keeps recurring:

"gerenciador de janelas" and it stumps Babelfish and FreeDict. Anyone know what it means?

hows the translation process going?

heres another great online translator:
[http://www.worldlingo.com/en/products_services/worldlingo_translator.html](http://www.worldlingo.com/en/products_services/worldlingo_translator.html)

---

### Post by Iandefor on 2006-07-25
> **yozef said:**
> hows the translation process going?

heres another great online translator:
[http://www.worldlingo.com/en/products_services/worldlingo_translator.html](http://www.worldlingo.com/en/products_services/worldlingo_translator.html) I've hit some snags. Mainly, I'm hitting phrases that actually require some kind of knowledge of Portugese, instead of Babelfish and an acceptable Portugese-English dictionary :). I've compiled a list of phrases I don't know how to translate, but I'll take another stab at them with worldlingo.

Thanks for the resources!

BTW, I'm just browsing for a few moments before I head back to bed (I had some communications to attend to on the forums), so if you want to help with the translation effort, here are a few choice phrases I could use help with:

> Copia diretorios e arquivos para a pasta /copy. 

As pastas copiadas para a pasta /copy serao colocadas na mesma posicao na imagem da distro. 

Assim, para colocar uma pasta em /user/local, na imagem, crie essa mesam estrutura (/usr/local) e coloque-a por inteiro na pasta /copy 

Na Na janela de dialogo que segue localize o diretorio que deseja copiar

Adicione scripts para rodar no boot de sua distro.\nNa janela de dialogo que segue localize o script que deseja que seja executado no boot.

Adicione pacotes .deb para serem instalados no boot de sua distro.\nNa janela de dialogo que segue localize o pacote .deb que deseja que seja instalado no boot.

Copie modulos principais para a sua distro.Na janela de dialogo que segue localize o modulo principal que deseja copiar.

Copie mini-modulos para a sua distro. Na janela de dialogo que segue localize o mini-modulo que deseja copiar

Descompactando utilizando o utilitario extract_compressed_fs

Voce nao possui o modulo cloop-utils instalado. Por favor, instale-o e retorne para  esta atividade

Descompactando utilizando o utilitario tar.gz

Informe o modulo principal que sera descompactado, no dialogo que abrira em seguida

---

### Post by RAV TUX on 2006-07-25
>  			 				Copia diretorios e arquivos para a pasta

 It copies directories and archives for the folder

---

### Post by RAV TUX on 2006-07-25
>  As pastas copiadas para a pasta /copy serao colocadas na mesma posicao na imagem da distro. 
 
The folders copied for the folder/CoPy serao placed in the same position in the image of distro.

I don't know what "serao" translates too?

---

### Post by RAV TUX on 2006-07-25
> Assim, para colocar uma pasta em /user/local, na imagem, crie essa mesam estrutura (/usr/local) e coloque-a por inteiro na pasta /copy 
Thus, to place a folder in/user/place, in the image, it creates this mesam structure (/usr/place) and places it in the folder entirely/CoPy


I don't think  /user/local should translated to /usr/place?

mesam I am not sure what this means?

---

### Post by RAV TUX on 2006-07-25
>  Na Na janela de dialogo que segue localize o diretorio que deseja copiar

In the one In the window of I dialogue that it follows locates the directory that it desires to copy

---

### Post by Iandefor on 2006-07-25
Thanks. Those translations are pretty convoluted, but I'll do what I can to get them making more sense.

---

### Post by RAV TUX on 2006-07-25
> Adicione scripts para rodar no boot de sua distro.\nNa janela de dialogo que segue localize o script que deseja que seja executado no boot.

It adds scripts to twirl in boot of its distro. \nNa window of I dialogue that it follows locates script that desires that is executed in boot.

---

### Post by Iandefor on 2006-07-25
> **yozef said:**
> It adds scripts to twirl in boot of its distro. \nNa window of I dialogue that it follows locates script that desires that is executed in boot. I don't want to be rude... but that's unworkable. I can't pull any elusive threads of meaning from that translation.

---

### Post by RAV TUX on 2006-07-25
> **Iandefor said:**
> I don't want to be rude... but that's unworkable. I can't pull any elusive threads of meaning from that translation.
   

I started to realize that the online translators are not very good. 

My apologies.

---

### Post by Iandefor on 2006-07-25
> **yozef said:**
> I started to realize that the online translators are not very good. 

My apologies. No problem :).

The online translators are okay for simple phrases, but these phrases seem to throw them a curveball.

---

### Post by richbarna on 2006-07-26
> **yozef said:**
> The folders copied for the folder/CoPy serao placed in the same position in the image of distro.

I don't know what "serao" translates too?

It means "should be" from the verb "Ser" (to be).

I work translating Spanish to English, and I must admit that this thread really made me chuckle :)

Do not trust online translators, most suck big style.

---

### Post by Iandefor on 2006-07-26
> **richbarna said:**
> It means "should be" from the verb "Ser" (to be).

I work translating Spanish to English, and I must admit that this thread really made me chuckle :)

Do not trust online translators, most suck big style. You'd be surprised at how well they can sometimes get the point of the sentence across, even if it uses totally improper grammar.

---

### Post by tseliot on 2006-07-27
Did you try this KIT?

> ROCK is a Distribution Build Kit.
This means it is a tool to create and maintain GNU/Linux distributions. With a
few keystrokes and some patience, you can have a generic distribution up in a
short time. With some more work, you can adjust its package selection.
With the help of freshmeat and the power of autotools you can add new
packages in a heartbeat.
What kind of distribution you will create, is limited by your imagination
and need.
[http://www.rocklinux.net/pipermail/rock-user/2006-July/000417.html](http://www.rocklinux.net/pipermail/rock-user/2006-July/000417.html)

---

### Post by Iandefor on 2006-07-27
> **tseliot said:**
> Did you try this KIT?


[http://www.rocklinux.net/pipermail/rock-user/2006-July/000417.html](http://www.rocklinux.net/pipermail/rock-user/2006-July/000417.html) Not yet. I'm still looking at MkDistro. If I can't get a decent translation done, I'll probably post what I have so far and move on.

Thanks, though.

---

### Post by Iandefor on 2006-08-07
There's another Ubuntu customization program out; it's called Reconstructor. Get the gory details [here]("http://reconstructor.aperantis.com/"). It's pretty easy to configure it; I'm running it right now, will report on how it goes. Heck, if it actually generates a usable ISO, I might even find a host for it!

---

### Post by RAV TUX on 2006-08-15
As I understand it the MKDistro has been translated by the Dreamlinux Devs, and is available for download:

[CENTER][FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2][COLOR=#ffffff]**MKDISTRO**                  [/COLOR][/SIZE][/FONT][/CENTER]
                             
          
        
                                  [[IMG]http://www.dreamlinux.com.br/english/imagens/mkdistro20.gif[/IMG]]("http://www.dreamlinux.com.br/downloads/mkdistro/mkdistro2.0.tgz")             [IMG]http://www.dreamlinux.com.br/english/imagens/space.jpg[/IMG]             [[IMG]http://www.dreamlinux.com.br/english/imagens/mkdistro25.gif[/IMG]]("http://www.dreamlinux.com.br/downloads/mkdistro/mkdistroUS/mkdistro.tar.gz")

---

### Post by Iandefor on 2006-08-15
> **yozef said:**
> As I understand it the MKDistro has been translated by the Dreamlinux Devs, and is available for download:

[CENTER][FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2][COLOR=#ffffff]**MKDISTRO**                  [/COLOR][/SIZE][/FONT][/CENTER]
                              
          
        
                                  [[IMG]http://www.dreamlinux.com.br/english/imagens/mkdistro20.gif[/IMG]]("http://www.dreamlinux.com.br/downloads/mkdistro/mkdistro2.0.tgz")             [IMG]http://www.dreamlinux.com.br/english/imagens/space.jpg[/IMG]             [[IMG]http://www.dreamlinux.com.br/english/imagens/mkdistro25.gif[/IMG]]("http://www.dreamlinux.com.br/downloads/mkdistro/mkdistroUS/mkdistro.tar.gz") Thank the gods. I'd given up in frustration.

---

### Post by nalmeth on 2006-08-15
Yes, reconstructor works quite well for what it does. 

It only supports ubuntu for now (thats only gnome), but it may work in a limited way with xubuntu. I'm going to try to test that this week.

Aparently version 1.0 is on the way (it's still beta ATM), so people should try it out and let Evan know what you find/think.

I haven't had as much luck with UCK, but have seen a couple new tools in this thread. Thanks for compiling them guys.

There is a lot on the horizon for distromaking it seems :)

---

