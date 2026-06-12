---
title: "Blender animation as interactive desktop background."
date: 2008-10-06
forum: New to Ubuntu
---

### Post by alsetcoil on 2008-10-06
Hello All!

First, I would like to thank all of you at Ubuntuforums.org . For years I have used this site for most of my Ubuntu issues. 
You all seem very knowledgeable and have been very helpful to me in many ways. 

My question is this, "Can I use a Blender rendering as an interactive desktop background"? 

By interactive I mean, can I interface with the desktop using speech recognition. The reason for this is I would like to develop a window session that uses an avatar I have created in Blender. This avatar will act as a "virtual assistant" with which I can communicate using speech.
I would like to be able to issue commands to an avatar such as:"Google Search...Ubuntu" and have it activate a series of commands needed to pull up a browser and go to google and search for Ubuntu. All while using some sort of animation to somehow instruct the avatar to "pull the application out of nowhere, and display it in front of the user magically" with stunning graphics. *(If this is too detailed for this this particular forum, I apologize, this is my first post. I am a little uncertain still on some of the rules and regs of posting here.)*

---

### Post by Nano Geek on 2008-10-06
That would be impossible without extreme modification to Gnome.
I don't think anything like that has been done.

---

### Post by alsetcoil on 2008-10-06
I haven't seen it done either. I have seen commercial deployment of this technology in corporate settings. I am willing to dedicate all my spare time to this project. Indefinitely. I just need to know what the next step is. 

So far, the project has these goals.

1. Create a virtual assistant or "digital companion" graphical user interface. The software should be able to work with the kernel of Ubuntu 8.04. 

2. Create a distributable operating system which includes and uses the new GUI. 


Computer operating systems today are very unfriendly. I want my computers to be more like very helpful friends. I want to speak to it, and have it speak back to me. I want it to remember preferences and previous conversations. I want to be able to give it verbal commands and have it respond quickly and accurately. When I walk in front of my computer it should know who I am by my face. It should say hello to me. Tell me about the weather. Tell me a joke...  When I look at my "desktop", I want to see an avatar who will bring up my programs from her hand, or something very similar. I know how to use festival to make the computer speak. I have seen packages that talk about speech recognition in the description. I have also read many articles which refer to facial recognition for web cams but have been unable to find any open source applications available. So using Ubuntu, I have concluded that my computer can "see" and "hear" me. And is able to "speak" to me and I am able to "see" it. It seems as though I am nearly there. I just want to refine and bundle these apps together to make a new window session. I don't really want to redesign Gnome. I want to make a new window session where the only GUI is a talking avatar, with a command line at the bottom, for when the voice-recognition is unable to perform certain functions. I still want to be able to launch a web browser so I do realize I will need a window manager of some sort. 

I do not feel like anything is impossible when it comes to open-source. It just takes a long time to accomplish great things. I never would have believed 10 years ago, that I would be choosing Linux over Windows. It's come a long way baby. If I would like to see this goal achieved I believe others do too. Linux error messages already have a sense of personality...They say things like "I cannot perform this action" this is a much more human response than "The system is unable to perform this action".  It appeals to me greatly. And I would like to see more development in this area.

---

### Post by ellgor on 2008-10-06
Hi, 

You have my full support in this venture, whilst not a programmer I can understand the thinking behind your venture.
Why can't an operating system handle such a (mediocre)? task as opening a web browser, when you tell it, the software is already there in speech programmes and whathaveyou, a little more attention to detail and it will happen.
As said I'm not a programmer, I do have a good grasp of the English language though, so if thats any use to you, contact me at: <removed>.

Regards, Ellgor.

---

### Post by shifty_powers on 2008-10-06
seriously, don't put your email in a public post, you're just asking for mountains of spam...

---

### Post by Steveway on 2008-10-06
I'll give you a tip for the next step you need to take.
a) Pay a developer to program this for you. (very expensive)
b) Learn one or more programming languages and start programming (cheap but takes a looooong time)
So see you soon (well not to soon ;)) when you accomplished this step.

---

### Post by alsetcoil on 2008-10-06
Thanks guys.

Steve, I definitely cannot pay for development at this time. Can you suggest any specific languages I should learn to work toward this goal? 

I do realize this is a project that could take a decade or more to come to fruition. Especially considering how few people it has and the lack of funding.

I have already spent ten years thinking about this system. Since I was kid I always wanted my computer to be able to actually communicate with me. I mean, yes, there was input/output, but it was just not the way I wanted to have it. 

I think, if I can gather enough like-minds on this, we can really see some interesting results. I just don't really have anyone around me who even knows what I am talking about or why I care... I am doing local group searches in my area but the only peeps who share my interests are in college... Which apparently contains the majority of people who know anything about that which interests me. Things like, building my own cluster computer with my 18 PCs for a render farm. But I do not go to college. (probably not a good thing for a having such a broad vision). So I go to the internet to find people who may have the same interests.. So far the smartest people nicest enough to talk to me are right here in these forums . Thankfully.

---

### Post by durand on 2008-10-06
The desktop background thing can be done with xwinwrap pretty easily.. Command execution shouldn't be too hard either. The really, really difficult bit is finding a speech recognition program. You can use festival for text to speech. I guess you can try dragon speech recognition in wine and get it to output text which you can then parse and act upon but I'm not totally sure...

---

### Post by Steveway on 2008-10-08
If you don't know any programming yet then you should first learn python, together with for example pygame you can make something pretty very fast.
Since you want to do things like speech-recognition and something like an ai you should make youself comfortable with neural-networks. I just got two books from the library yesterday, one is about neural-networks by Soren Brunak and Benny Lautrup and the other one is called Gödel, Escher, Bach, I think I shouldn't have to tell more about that one.
Oh, and for artificial intelligence you should also look at Lisp, even if you won't use it for your project it will help you.
EDIT: And don't forget to read the stickys at the programming-section of the boards.

---

