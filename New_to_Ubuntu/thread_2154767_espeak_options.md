---
title: "espeak options"
date: 2013-06-15
forum: New to Ubuntu
---

### Post by kom333 on 2013-06-15
Hello lovely GNU/Linux users!

I have been wondering how to change some options in espeak. I found out about command: ```
espeak -h
```, that allows me to see list of options. That' s ok, but I need to change some of them, if it is possible. 
If someone knows how to solve this, I would be grateful.

---

### Post by Impavidus on 2013-06-16
Just add them on the command line, like you added the -h option. For example, to pronounce the file "example.txt" at slow speed and save the result as "example.wav", give the command```

espeak -f example.txt -s 120 -w example.wav
```
These options work the same way in almost all programs.

---

### Post by kom333 on 2013-06-16
Impavidus, I tried what you said and I got message in terminal:" Failed to read file 'story.txt' ". :( So questions are what is that story.txt and where is located? 
And I think you didn't understand me completely...All I  want is to speed down pronunciation and language, if possible.

---

### Post by Impavidus on 2013-06-16
The filename story.txt was just an example. I shall make it clearer in my previous post.

You can use the command```
espeak --voices
```to get a list of voices. Each voice is made for a specific language. In my case the output starts with```

Pty Language Age/Gender VoiceName       File        Other Langs
 5  af             M  afrikaans         af          
 5  bg                bulgarian-test    bg          
 5  bs             M  bosnian           bs          
 5  ca             M  catalan           ca          
 5  cs             M  czech             cs          
 5  cy             M  welsh-test        cy          
 5  da             M  danish            da          
 5  de             M  german            de          
(...)

```Find the language you want (for some languages there are a few variants) and then use the voice name on the command line. With the -s option you can set the speed in words/minute. For example, if you want to pronounce the file example.txt at 120 words/minute and it contains german text, use```

espeak -f example.txt -s 120 -v german
``` Substitute the values you want. Also note that you don't have to supply a file name, as there are other ways to provide the text you want pronounced.

Alternatively, if you are uncomfortable with the command line (and I get the impression you are), you can install **gespeaker**, which is a program available in the software centre. It's a graphical front end to espeak, where you can change the settings you want with sliders and menus. It may be better suited to your experience.

---

### Post by kom333 on 2013-06-17
F*ck! I didn't read your post carefully and now i look like a fool in your eyes. :( i just copied the code that you gave me and pasted it in terminal.
To me, CLI is better than GUI and i prefer it :)

So you are telling me i must make .txt file and save it somewhere and then open it in espeak, right? :)

---

### Post by Impavidus on 2013-06-17
Can happen.

espeak accepts text from a file, from the command line or from standard input (which may be a pipe):
```

#From file:
espeak -f example.txt <other options>
#From the comand line
espeak <other options> "Text to be pronounced"
#From a pipe
command_that_writes_text | espeak --stdin <other options>
#From stdin
espeak --stdin <other options>
Now type the text or paste it to the terminal.
Close with ctrl-d on an empty line

```
espeak also knows how to handle html files, in case you're dealing with those. I don't know where the text you're dealing with comes from.

---

### Post by LinuxUser666 on 2013-06-17
Hello bros...umm does that apply for text in .pdf format?
Just curious.

My regards. Stay sharp. Especially you kom333 :KS

---

### Post by kom333 on 2013-06-17
Well, Impavidus thank you. You helped me a lot :)

---

### Post by HiImTye on 2013-06-17
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
espeak also accepts text entered as an unswitched variable as input, i.e.```
espeak -v en-uk 'this is some speech. I am very smart.'
```
notice how in my example, I gave the language name (en-uk) instead of the voice name (english)

---

### Post by Impavidus on 2013-06-17
> **LinuxUser666 said:**
> Hello bros...umm does that apply for text in .pdf format?
Just curious.

My regards. Stay sharp. Especially you kom333 :KS

[Manual](http://espeak.sourceforge.net/) says plain text and html. I would be surprised if they ever include support for pdf, except when using a pdf to html converter as a filter. Html contains text with a logical structure, from which your web browser generates the visual structure that humans, but not computers, can easely recognise. Pdf contains visual structure, from which it's very difficult to reconstruct logical structure if you're not human. To be able to emphasise the right words, put in the right pauses, skip footnotes et cetera you need to understand the logical structure of the text.

---

### Post by LinuxUser666 on 2013-06-22
Thank you for your information about pdf...although it kinda crushed my hopes and dreams about it reading me Linux Bible :( ahh well...
Many thanks to you and the Ubuntu community.
kom333 don't forget to mark this thread solved, keep forums clean :)

My regards, stay brutal. :p

---

### Post by kom333 on 2013-06-23
Don't worry, I will mark this thread solved ;)

---

