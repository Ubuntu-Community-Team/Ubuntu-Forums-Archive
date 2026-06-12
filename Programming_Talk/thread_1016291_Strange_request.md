---
title: "Strange request"
date: 2008-12-19
forum: Programming Talk
---

### Post by johnno56 on 2008-12-19
I have a Vocabulary Quiz program, writen in QBasic that I conveted from TRS80 Basic, and I want to update it with a GUI. I am not a programmer of C (or its variants), Glade etc but would like to have it look at least pleasing to the eye. ASCII can be sooooo boring.

I know that this request may sound strange or vague, but I would like to try and modify the programme. Any tips, hints, suggestions, applications etc would be appreciated.

I am not asking anyone to write it for me. I am just asking for help so that I can do it myself.

If I have submitted this request to the wrong area, please let me know.

Regards

J

---

### Post by mssever on 2008-12-19
> **johnno56 said:**
> I have a Vocabulary Quiz program, writen in QBasic that I conveted from TRS80 Basic, and I want to update it with a GUI. I am not a programmer of C (or its variants), Glade etc but would like to have it look at least pleasing to the eye. ASCII can be sooooo boring.

I know that this request may sound strange or vague, but I would like to try and modify the programme. Any tips, hints, suggestions, applications etc would be appreciated.
You'll have to learn an appropriate GUI toolkit for your program. As far as I know, QBasic isn't available on Linux, so you'll be stuck with Windows and its tools unless you rewrite it in a modern, non-BASIC language.

Glade is for GTK, so you have to use a language that has GTK bindings if you want to use Glade.

---

### Post by ghostdog74 on 2008-12-19
> **johnno56 said:**
> I have a Vocabulary Quiz program, writen in QBasic that I conveted from TRS80 Basic, and I want to update it with a GUI.
Just a suggestion. You can use the browser as your basic "GUI". you can create checkboxes, radiobuttons, buttons, etc. For data processing, you can use PHP, (or others.)

---

### Post by johnno56 on 2008-12-20
MSServer,

I have had a very brief look at Glade 3 and tried out an example program, a URL Manager, and found it easy to follow. Undersanding the syntax is another story, but I am sure with time, I will get the hang of it.

Ghostdog74,

I am quite proficient creating web pages, but know nothing about passing data from a source to html. I am unfamiliar with PHP and what it can and cannot do.

Thanks guys for your suggestions. Looks like I have a mountain of reading to do.

Much appreciate your time in replying.

Regards

J

---

### Post by mssever on 2008-12-20
> **johnno56 said:**
> MSServer
My nickname is mssever, not MSServer. It has nothing to do with Microsoft servers. :)
> I am quite proficient creating web pages, but know nothing about passing data from a source to html. I am unfamiliar with PHP and what it can and cannot do.Passing data to HTML is easy. You just print your program's output as HTML. PHP is tuned for this task, but there are many other options, as well. My personal preference these days is Python + Django. One thing you need to be aware of, though, is that the server you host your pages on has to support whatever language you use. PHP support is easier to find than Python support.

---

### Post by johnno56 on 2008-12-21
My appologies for the nickname confusion. Old habits die hard.

Thank you for the suggestions. Only problem is that I do not have a host server. I was planning on use it on my Pc and if it worked out okay, I would create a multi-OS executable.

I am not familiar with passing data. I am used to reading info from data statements or reading from a text file, processing info to display on the screen. I am sorry if this method is too old, but it's the only one I know, at the moment.

I am not familiar with PHP, Python or Django. I'm not even sure if I know what they are. Can you recommend books, tutorials, examples etc ? I have very few programming skills. I have been using Basic since the early '80s. I figured that it's about time to 'upgrade'. Any suggestions or recommendations would be appreciated.

Again, thank you for replying so quickly.

Regards

J

---

### Post by mssever on 2008-12-21
> **johnno56 said:**
> I am not familiar with PHP, Python or Django. I'm not even sure if I know what they are. Can you recommend books, tutorials, examples etc ? I have very few programming skills. I have been using Basic since the early '80s. I figured that it's about time to 'upgrade'. Any suggestions or recommendations would be appreciated.
PHP and Python are both programming languages. Django is a web application framework written in Python. (Django might be more difficult to learn than PHP, as far as making websites goes. However, PHP makes it really easy to write unmaintainable code.) pmasiar has some great links in his signature for learning Python. For both PHP and Python, if you visit their respective websites you'll find tutorials and documentation. Your input/output questions will be answered quite easily if you work through an appropriate tutorial.

---

### Post by ankursethi on 2008-12-22
Are you sure you want to jump into web development? I mean, writing code for the web might be easier, but actually setting up the environment can be pretty frustrating. What if you want to show your app to your friends? You'll either have to set up a server on their PCs, or keep your own PC turned on so that they can use your IP address to see the app hosted on your PC, or purchase web space to put the app online. All in all, web programming is not a good choice at this stage. Web programming is a seriously bad place for someone to begin experimenting with programming.

Why not learn Python or Ruby? Since you want to code a GUI very quickly, and it doesn't need to be too complex either, I'd suggest Ruby along with the Shoes toolkit ([http://shoooes.net](http://shoooes.net)). Why's Poignant Guide to Ruby is a good place to begin learning the language ([http://poignantguide.net](http://poignantguide.net)).

BTW, people will also suggest you learn Python. Python is an equally good choice, and has a much larger standard library and better documentation than Ruby (I'm a Python guy myself, and know little Ruby). The reason I did not suggest Python is because Python does not have a toolkit to rival Shoes. There's the obvious choice, Pygame ([http://pygame.org](http://pygame.org)), which is a great game programming library, but it's much more complex than Shoes and contains many features you might not need in your quiz application (do you want joystick controls?).

To sum up, the two most popular choices for hobbyists starting out in the programming world are Python and Ruby. Do a little research and choose the one language you like. You can't go wrong if you learn either one of them.

---

### Post by mike_g on 2008-12-22
You dont necessarily need PHP, Python or MySQL to create a browser based quiz app. The data can be laid out in XML and the scripting can be done client side with Javascript.

---

### Post by johnno56 on 2008-12-23
Python, Ruby, PHP, XML, Javascipt....  The mind boggles.

I suppose I have brought this upon myself. I did ask for help.

In a nutshell is my problem:

I am converting a qbasic to a liberty basic, vocab quiz with the words and definitions stored either within the program or via an external text file. The word is chosen randomly and displayed on the screen with the correct definition and four other definitions. Selection is made and after a pre-arranged number of words, a rating or score is given. Play again yes or no. That's it. I just need to know which application would be best to display this type of game? I would prefer a GUI if possible.

Liberty basic was chosen to cope with the extra string space required.

I am sorry if this request is too noobish, but I have to start somewhere.

If you need to look at the code, let me know, and i'll email it. (15,000+ words and definitions are a bit much to display in the forum.)

Regards

J

---

### Post by ankursethi on 2008-12-23
Liberty Basic seems like it's Windows only. If you use LB, your app won't run on Linux (at least not nativey).

As I said before, choose Ruby. It's simple to learn, and has a great library called Shoes which you can use to create simple GUIs quickly. Here's a simple example of a Ruby app which uses Shoes to display three buttons on a small window :
```

Shoes.app {
  stack(:margin => 4) {
    button "Mice"
    button "Eagles"
    button "Quail"
  }
}

```

It's that simple. Just take a look at my previous post for resources.

REMEMBER: don't get lost. If you choose something, stick at it for at least a month before giving up.

---

### Post by jacensolo on 2008-12-23
I've tried liberty basic when I first started learning how to program, and with all basic, it's just not a good idea. It becomes unmanageable and doesn't teach good habits. While there are some that aren't so bad (Dark Basic, Pure Basic), they have specific niches. 

If your code is mostly done, it maybe easiest to switch Liberty Basic. If a lot of changes are required anyway, I reccomend something else.

Normally I would suggest Python, my language of choice. But I think you should go with ankursethi on his one and use Ruby with shoes.Both Python and Ruby are about equal, but shoes seems to be what you are looking for. Besides, who wants to walk around with bare feet?

Repeating what ankursethi said, choose something and stick with it. I tried several languages before I things started clicking with me. I have been programming off and on for years, but not until I settled down with one language did I understand what I was doing and how it worked.

---

### Post by johnno56 on 2008-12-23
Thanks guys,

I hope I did not come across as preparing to give up. I have no intention of giving up. I was just overwhelmed with all the choices. I agree, stick with it for a month, just to see how I go.

Ok. I will try Ruby with Shoes - with or without socks? ;)

I want to thank you guys for all the help and advice. If I am correct, and most times I am, I will probably be pestering you guys again for coding advice, or something like that.

Regards

J

---

