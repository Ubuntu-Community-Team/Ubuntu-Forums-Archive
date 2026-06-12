---
title: "SPE python IDE: Call for testers!"
date: 2007-03-06
forum: Programming Talk
---

### Post by stani on 2007-03-06
[IMG]http://photos1.blogger.com/x/blogger2/2316/206766585062547/1600/z/21342/gse_multipart58221.png[/IMG]

I've been working a lot on fixing SPE and upgrading it with the latest plugins. The winpdb debugger no longer fails and wxGlade crashes are history. Is that not great? Are you eager to try it out yourself? Please do! Get it from subversion and test it for any critical bug, so I can iron it out. I have been patching a lot for Ubuntu users, who will be very pleased with this release, and I'd like to thank Jurjen a lot for his work on Mac issues. This is a definitely a release everyone should upgrade to, wether you use windows, mac or linux! SPE is both suitable for newbies and experienced python programmers.

Read more here:

[http://pythonide.stani.be](http://pythonide.stani.be)

Please comment on my blog and do not reply here.

Thank you!

Stani

PS I use SPE myself on Feisty and Edgy Ubuntu. Kubuntu testers are especially welcome to leave feedback on my blog.

---

### Post by stani on 2007-03-07
I forgot to update my blog. Now all the latest information about the coming release is there. Try it from subversion!

---

### Post by j_g on 2007-03-07
I've been using Dr. Python because it's cleaner, more streamlined UI seems more intuitive to me than other alternatives, including SPE.

What about SPE have you changed that makes it better (than the alternatives) for an Ubuntu user in particular?

I don't use wxPython, but I do use pyGtk. What, if any, advantage does SPE have (over alternatives) for creating a Python script that uses pyGtk?

---

### Post by etank on 2007-03-07
The one thing about SPE that turns me away (even though it is a small thing) is that there is no support for printing. I like to print my code to be able to go over it at times when I am not at a computer.

---

### Post by pmasiar on 2007-03-07
> **j_g said:**
> cleaner, more streamlined UI seems more intuitive to me 

What for you seems be "cleaner UI" for me looks like editor severely  lacking many interesting features. DrPy is based on SciTE and you can feel it. I like SciTE and use it for simple edits, but SPE has some very nice features (missing in SciTE and DrPy) like:
- indent guide. I really tried to find in in DrPy and make it work but no luck. It is just a "must have" feature for a language like Python where indent has syntax meaning
- DrPy bookmarks are over-designed. SPE uses ##--- or ##xxxx code tags comment as permanent bookmark - and shows them in left source outline panel, very convenient
- syntax checker in SPE notifies by color wrongly matched quotes in strings. Extremely convenient.
- don't get me started on DrPy syntax coloring. Syntax style editor is broken in my Ubuntu box - and I do not see point wasting time by trying to fix it.

I could not force myself to try DrPy long enough - even brief comparison unveiled gaps in features which I am not willing to tolerate. For editor used to big part of my work, I prefer rich functionality of SPE. I use and like spartan SciTE to edit simple text files.

IMHO, YMMV. Preferences and style is very personal taste indeed.

Diverting discussion this way feels like hijacking thread, and we have sticky to discuss IDEs. j_g, if you want to continue discussion in comparing IDEs, let's continue in  sticky about IDEs, and let's let this thread be about SPE testing.

Maybe Stani will answer your questions about deeper differences. :-)

---

### Post by j_g on 2007-03-08
Obviously, there are some features that Dr Python doesn't have, but alternatives do have. But I don't judge a toolset based upon its features alone. In fact, when it comes to dev tools, I often favor a more rudimentary featureset that is more intuitive and efficient than one that is just too difficult to use because its interface/design is too convoluted, piecemeal and poorly integrated, and/or inefficient.

But, if a tool has a particular feature that is very important to me, I may be willing to overlook flaws in its overall implementation.

I had already rejected using an earlier version of SPE over Dr Python based upon criteria I mention above. Now, I'm told that there is an "improved" version, and the OP is openly asking the readers here to try/test it. My preceding post asks about some _specific features_ that _may_ make a difference in my evaluation of this particular offering (whereas other features may not make any difference at all). That post is definitely on-topic, despite your suggestion otherwise, and it certainly wasn't a discussion of unrelated IDEs/topics either. Is this thread not specifically and entirely about this version of SPE? So were my questions.

A person shouldn't have to install a piece of software to find out some information he wants to know about it. Otherwise, what the heck are these forums here for? Just for people to post C code that is deliberately unreadable??? I'm not looking to find out who likes which IDE best. I could care less about that. I want to know if this new version of SPE has something new to suit _my_ needs. As such, a request for such information would be very off-topic in a sticky thread about "IDE popularity" rather than this version of SPE.

By "indent guide" I assume you mean some sort of visual, horizontal line that shows you the current indentation from the left margin. Yes, in a language like Python, which enforces a strict rule about such whitespace, that could be useful. But I'd have to know more specifically about how it was implemented in this particular program to ascertain whether that trumps some of the other UI/usability issues. Probably wouldn't be that important to me, as your other noted features aren't. But definitely, the answers to specific questions I raised could be an impetus that makes me give it another test drive. And that appears to be entirely what the OP started this thread to exhort.

---

### Post by stani on 2007-03-08
> j_g: What, if any, advantage does SPE have (over alternatives) for creating a Python script that uses pyGtk?
SPE has no support for pyGtk, as this feature was never requested. SPE itself is strictly speaking is only an editor, but which collaborates with other open source projects such as gui designers (wxGlade, XRCed,...) and debugger (WinPdb) to turn more into an IDE (integrated development environment). Recognizing the quality of these projects and instead of reinventing the wheel it integrates interaction with them inside SPE. For example if you want to debug a file, you don't need first to find out how to start the debugger and then to open a file in it, but with one click you can launch the debugger from within SPE. 
That said, if you can point me to some nice tools for pyGTK, I would be happy to integrate interaction with them as well. Glade maybe? I don't use pyGTK myself, but if pyGTK developpers would give me constructive feedback I could do something for them. If they just complain there is nothing for them, you can't expect action from me.
Differences with DrPython (or alternatives) are realtime syntax error underlining, which is both handy for newbies as experienced programmers, realtime updating of the class explorer, UML (drawing a printable scheme of your code to get better overview), a debugger which can handle threads, ... to name a few. If you think of developping a GUI application you will need threads sooner or later and probably you like to have a debugger which can handle it. The debugger until now was not working on Ubuntu, now it does. If you don't need it, fine. Besides that I noticed that SPE was not running fine on Ubuntu as it should be. As I know quite a lot of people on Ubuntu are using SPE (there is even an edubuntu lab), I strongly advise everyone to check out the next version and give me feedback so I can improve it. 

> etank: The one thing about SPE that turns me away (even though it is a small thing) is that there is no support for printing. I like to print my code to be able to go over it at times when I am not at a computer.
Black & white printing should not be so hard to implement. Does it matter for you if it is color or not?

> j_g Is this thread not specifically and entirely about this version of SPE? So were my questions.
This call was to people who are interested in SPE and want to test. It is not a release announcement. Compare it with people needed to test Feisty.

I think that pmasiar was not so happy with the negative tone in your posts. Some people take another approach, they file feature requests to get some sofware adapted to their needs. If you want to stimulate developpers of software you (might) use, I also advise you to be more positive.

---

### Post by pmasiar on 2007-03-09
> **stani said:**
> Black & white printing should not be so hard to implement. Does it matter for you if it is color or not?

Black & white will be enough and important to have. Thanks!

---

### Post by stani on 2007-03-13
For the upcoming release there is a feature freeze. I will have a look afterwards to add printing.

---

### Post by WW on 2007-03-13
Stani,

I went to your subversion page to download the latest version.  Unfortunately, there is a box labeled "15 diggs" that covers up part of the instructions for getting the program from your subversion repository.  I have attached a screenshot that shows the problem.  Resizing the browser window didn't help.

I am using Firefox 1.5.0.10 in Ubuntu Dapper.

---

### Post by siman on 2007-03-13
great! i appreciate, that you take the time to fix so many spe bugs, especially for ubuntu.

i'd like to help, to make it easy for me: can you post svn and bugtracker url, so i can dive right in (i could look up the project page.. but since this is the tester-thread this info would make sense)

(now that i think about, there is this one bug which annoyed me most: pasting with strg+v while the autocomplete dropdown was visible crashed spe... would like to check wether that was fixed. i'm already so usd to it, that i always press ESC before strg+v :-)

---

### Post by stani on 2007-03-13
> **WW said:**
>  Unfortunately, there is a box labeled "15 diggs" that covers up part of the instructions for getting the program from your subversion repository. 

Thanks for reporting! Is this better? 

@siman

> can you post svn and bugtracker url

Just to copy and paste this in the terminal:

```
svn checkout svn://svn.berlios.de/python/spe/trunk/_spe
```

This will create a '_spe' folder.** Do not rename it to 'spe' or another name!** From this folder you can run:

```
python SPE.py
```

Please report bugs directly by email as I am fixing bugs now and this goes more fast, especially for feedback and trying out things. My email address is spe.stani.be*g ma il # co m. (Sorry that I have to use spam techniques to protect me against spammers.)

Please be sure you first removed your old SPE:
```
sudo apt-get remove spe kiki wxglade
```

You can test if it is properly removed by checking the path:
```
import _spe
print _spe.__file__
```
This should point to your subversion path.

---

### Post by DC@DR on 2007-03-13
It looks impressive, I will definitely give it a try, right now! Cheers :)

---

### Post by WW on 2007-03-13
> **stani said:**
> Thanks for reporting! Is this better? 
Yes, thanks for the quick fix.

---

### Post by stani on 2007-03-18
> **WW said:**
> Yes, thanks for the quick fix.
You're welcome. For everyone who wants to follow the development of SPE, subscribe to:
[https://lists.berlios.de/mailman/listinfo/python-spe-dev](https://lists.berlios.de/mailman/listinfo/python-spe-dev)

You are also welcome to post bug reports against subversion there.

```
svn checkout svn://svn.berlios.de/python/spe/trunk/_spe
```

Stani

---

### Post by 55Rebel on 2007-07-29
OS: Ubuntu 7.04 - Fiesty Fawn

Installed spe via synaptic package manager.
When installing, there was a note that wxgtk2.6 was NOT AUTHENTICATED.

When I try running program, all i get is a white box that briefly pops up, and that's it, nothing.

Any clues?

Thanks

---

### Post by tc101 on 2007-07-30
I originally installed SPE using synaptic package manager.  Can I use that to upgrade to the new version? Is so how?  If not, what is the best way to upgrade.

Obviously I am new at this.  I have very little experience installing and upgrading other than with synaptic package manager.

---

