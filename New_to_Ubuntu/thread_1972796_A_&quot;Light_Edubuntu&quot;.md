---
title: "A &quot;Light Edubuntu&quot; ?"
date: 2012-05-03
forum: New to Ubuntu
---

### Post by Oscar Rojas on 2012-05-03
Hello Ubuntu community!

I am new to this forum. Hope to be in the right place to comment my project. If not please tell me where should I go...
 

My son has an old Compaq desktop that he wants to dedicate as a PC for my four grandchildren. He have asked me to help him in this project. I am a retired System Engineer and have plenty of time; however my background does not include Linux.
 

I have read some reviews about Linux for Kids. Edubuntu fits most of the features we are seeking, however after installing Edubuntu 12.04, I found it is too heavy for my old PC: it took about one minute to launch a simple program and the disk is continuously working... it seems to me that the system is paging or swapping memory a lot.
 

I also tried some variants of "mini distros for kids". They installed and ran pretty well in my PC, but they offer a limited set of applications and have a rigid, not customizable environment.
 

So I am looking for a light but standard Linux distribution, satisfying most of our "wishes" via pre-packed software or compatible applications that I could acquire/download later.
 

I have read about Lubuntu. It sounds to be the right distro for my project, but I am afraid I will lose the rich set of applications bundled in Edubuntu. So what I seek is something like a "Light Edubuntu" :). Lubuntu includes a Lubuntu Software Center customized for Lubuntu, but I don't know if all applications bundled with Edubuntu are available there.
 

In summary my questions are:

[LIST=1]
[*]How well Lubuntu performs in a little PC like mine? (Pentium 4 2.4 GHz, RAM 487.7 MiB; HD 39.4 GiB)
[*]Which of the functions provided by applications bundled in Edubuntu are not supplied by apps. listed in the Lubuntu Software center? 
What I am trying to figure out is which functions (in particular functions that are interesting in a kids learning/playing/working environment) am I loosing while switching from Edubuntu to Lubuntu. Note that I said "functions", not "applications".By example, I don't care which browser comes whith it... but it should be compatible with some parental control tools.
[*]Which is the right forum or mailinng-list to request for help on specific doubts once I start using Lubuntu?
[/LIST]

We welcome any comments from users who have experience setting up this type of environment for children in small PC's.
 

Thanks in advance for your attention.
 

Oscar Rojas
Costa Rica

---

### Post by marinara on 2012-05-03
really you're asking edubuntu questions, but your question prefix is lubuntu.  I don't know how software installation on edubuntu works, but I assure you there's a way to do it, and lubuntu should work on your hardware.  since you have low ram, please download the alternate cd

---

### Post by wildmanne39 on 2012-05-03
Hi, lubuntu uses the same repositories as all other versions of ubuntu so you can install all the same software but remember the more you install the more resources lubuntu will use.
Thanks

---

### Post by Oscar Rojas on 2012-05-04
Thanks Marinara,
 
Indeed my questions are related to both Lubuntu and Edubuntu... But due that only one prefix is allowed I choose Lubuntu that is the distro I am trying right now.
 
I already installed Lubuntu from the regular desktop CD. I have defined the user accounts for the kids and started to try some programs and figure out how to personalize the desktops for each one. So far the performance is really good, definitively faster than Edubuntu... So, my first question is solved.
 
The second is the main question crossing distros: 
The educational packages bundled with Edubuntu may be downloaded and installed individually. I noticed that there are two versions of the packages: (1) the regular version, intended for Ubuntu distros using Gnome and (2) the KDE versions for Kubuntu. But Lubuntu uses LXDE instead. I see no version of these packages for LXDE. So I am afraid these applications won't run on LXDE. 
May be I have to install Gnome and use it instead LXDE, so I can use the regular educational packages... but I am afraid that Gnome will burn more processor or storage resources than LXDE and the overall performance will be affected.
 
As you see, I am novice in Linux and this world of several distributions with different desktop software is confusing for me. I ignore if the difference is just the user interface, or if the application interface is affected too. In the second case the applications are not portable from one desktop environment to another. That is my theoretical doubt.
I could try to find an answer by actual test... and in the last case that is what I will have to do... but there are lots of applications and I will appreciate if some body can tell me if there is a list of applications already tested and guaranteed to run under Lubuntu.
 
Thanks again

---

### Post by Oscar Rojas on 2012-05-04
Thanks Wildmanne, 
 
There is a single software repository for all Ubuntu distributions... Right, but the fact that an application can be installed does not guarantee that it runs. May be it requires some features from regular Ubuntu not available in Lubuntu. Please see my entry #4 in this thread about this trascendental doubt.
 
You advice: "the more you install the more resources Lubuntu will use". Again, I am new in Linux and ignore the technical details about its operation... I thought that installed applications does not use resources (besides their residence in HD) while they are not in operations... but your advice gives the impression that by the mere fact of being installed they are consuming resources... May you please clarify?
 
Thanks for your attention.

---

### Post by Bucky Ball on 2012-05-04
Any package you install should also drag in the dependencies. This will probably mean Gnome and possibly ubuntu-desktop which could leave you at square one again; with a sluggish machine.

---

### Post by MG&amp;TL on 2012-05-04
> **Bucky Ball said:**
> Any package you install should also drag in the dependencies. This will probably mean Gnome and possibly ubuntu-desktop which could leave you at square one again; with a sluggish machine.

...not if you don't load the dependencies. Lubuntu willl still be quick with ubuntu-desktop installed. I imagine it's zeitgeist &co. you have to worry about.

@OP: I suggest you keep doing what you're doing and installing apps.  *buntu has package management, which means that any missing dependencies of a program are installed as well.

---

### Post by wildmanne39 on 2012-05-04
Hi, Bucky Ball clarified for me, when you install the applications you want for edubuntu then it will most likely have a lot of dependencies that will automatically be installed which will in turn tax your resources more putting back to where you started.
Thanks

---

### Post by marinara on 2012-05-04
to the orgininal poster:
LXDE is based on Gnome, you didn't know this when you asked your question.

You can also install KDE apps, but this causes the system to use more memory

---

### Post by Bucky Ball on 2012-05-04
> **marinara said:**
> 
LXDE is based on Gnome ...



It is? Can't find anything about that ... have you a link?

---

### Post by MG&amp;TL on 2012-05-04
> **Bucky Ball said:**
> It is? Can't find anything about that ... have you a link?

It is. It uses Gtk+, which is gnome's graphical toolkit. However, we don't use its window manager or other toolkits.

---

### Post by Bucky Ball on 2012-05-04
> **MG&TL said:**
> It is. It uses Gtk+, which is gnome's graphical toolkit. However, we don't use its window manager or other toolkits.

Cheers. Interesting ...

---

### Post by grahammechanical on 2012-05-04
@Oscar Rojas

launch the Software Centre in Lubuntu and search for Edubuntu. What do you see?

In standard Ubuntu I see

Pre-school bundle
Primary bundle
Secondary bundle
Tertiary bundle.

These are applications grouped according to the ages of children. By installing them as package through the Software Centre you can removed them as a package through the software centre.

I hope that this helps you.

You could also consider installing Edubuntu onto a USB memory stick with persistence and running from that. I did this for a friend so she could use it with her little girl.

You could also try Edubuntu Weblive

[http://edubuntu.org/weblive](http://edubuntu.org/weblive)

For 2 hours over the Internet.

Regards.

---

### Post by SteveDee on 2012-05-05
> 
LXDE is based on Gnome, you didn't know this when you asked your question.



> **MG&TL said:**
> It is. It uses Gtk+, which is gnome's graphical toolkit. However, we don't use its window manager or other toolkits.

I think this is misleading. GTK is a dev toolkit (like Qt) maintained by the Gnome Foundation. The statement "LXDE is based on Gnome" is incorrect. ([http://en.wikipedia.org/wiki/GTK%2B](http://en.wikipedia.org/wiki/GTK%2B))

---

### Post by MG&amp;TL on 2012-05-05
> **SteveDee said:**
> I think this is misleading. GTK is a dev toolkit (like Qt) maintained by the Gnome Foundation. The statement "LXDE is based on Gnome" is incorrect. ([http://en.wikipedia.org/wiki/GTK%2B](http://en.wikipedia.org/wiki/GTK%2B))

Depends on your point of view. I should expand on my previous answer...

LXDE has its own bespoke set of of software (panels, sessions, etc.), which for its graphical bits  uses Gtk in one of its guises (python-gi, Gtk+, Gtkmm, Vala).  A default LXDE install is almost entirely based on Gtk.

Therefore, you could say "LXDE is based on Gtk"-but "being based on GNOME" is misleading, I agree. LXDE doesn't use mutter, shell or similiar technologies. In fact, we're only just coming around to Gtk 3.

Hope that clears things up a bit. (not sure who you were implying was misleading, SteveDee). :)

---

### Post by Oscar Rojas on 2012-05-06
Thank you very much to all people helping me in this project.

Let me tell you about my progress:

I installed the educational bundles via the Software Center. Installation was easy and quick. New applications are now included in the Education and Games menus. I am testing them and all seems to work pretty good, most functions are OK (see below for exceptions) and they run fast enough.
In fact, I opened a task manager in the second desk and the CPU and storage utilization are really low for every application I tested.

Then, my second original question is solved and the answer is: yes, Ubuntu educational bundle works pretty good under Lubuntu and have not dragged resource-burning dependencies.

Now is time for my third original question:
Where may I post punctual question reporting malfunctions, or things that I want to do and found no answers in the forum archives?
Below are some samples of such questions: (I am not asking for replies here in this thread, just listing them to illustrate my general question)
a) No sound at all in any application.
b) Some applications do not close. If reopened, another instance is launched.
c) Khelpcenter is not installed by Software Center, I had to use Synaptic to install it.
d) I want to put pictures of the kids in the login panel.
e) I need different applications menu for each kid.
... and so on...

I guess the best way is to start a new thread for each issue, my question is in which forum?

Again, thank you very much for your time helping me.

Oscar Rojas

---

### Post by linuxmatt7 on 2012-05-06
What you might want to do is use Xubuntu, and install some applications similar to the Edubuntu applications. This way you get something like Edubuntu only with a Xubuntu UI.

Now if Xubuntu is to heavy than you might want to try the same as listed above only with Lubuntu instead of Xubuntu. If Lubuntu is still to heavy I do not know what to tell you.

---

### Post by Bucky Ball on 2012-05-06
> **linuxmatt7 said:**
> What you might want to do is use Xubuntu, and install some applications similar to the Edubuntu applications. This way you get something like Edubuntu only with a Xubuntu UI.

Now if Xubuntu is to heavy than you might want to try the same as listed above only with Lubuntu instead of Xubuntu. If Lubuntu is still to heavy I do not know what to tell you.

OP is already running Lubuntu fine with educational apps.

@ Oscar Rojas: Yes, post a thread for each issue. General Help would be fine. As for putting picture of the kids at login, easiest tool I've found is Grub Customizer:

[http://www.webupd8.org/2010/10/grub-customizer-lets-you-reorder-add-or.html](http://www.webupd8.org/2010/10/grub-customizer-lets-you-reorder-add-or.html)

Lets you do all sorts with your login.

For different menus you would need to create a user for each child. Not sure how you would achieve different menus once that's done or if it's possible, though. Guess you could do three installs, each tailored to each individual, and they select the appropriate install at boot, but there might (must?) be a better way ... hopefully someone who knows will pipe up but I advise posting new threads about your issues. You will have better luck than having them buried here.

Good luck. Post links back here if you want ... ;)

---

### Post by Oscar Rojas on 2012-05-07
Thanks Bucky Ball and previous repliers.
 
Be here I am declaring this thread solved.
 
I am going to document my pending issues to post them as individual threads. 
 
Hope to "see" you again in General Help forum.

---

### Post by Bucky Ball on 2012-05-07
Cheers and good luck with it. ;)

---

