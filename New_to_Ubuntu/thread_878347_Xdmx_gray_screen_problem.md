---
title: "Xdmx gray screen problem"
date: 2008-08-02
forum: New to Ubuntu
---

### Post by KIPIK on 2008-08-02
I all,
      I'm playing with my new toy: LINUX! and I've discovered a little program: Xdmx. I have a hard time making it work and I need help. Here it goes:

I tried a lot, read a lot, google a lot and still, I can't make it work. I'm able to connect to another computer but I'm unable to make a Window Manager(like TWM) to appear. All I can see is beautiful gray screen with an 'X' in the middle that we can call a mouse cursor(it move but since there's nothing to click on...) Here is what I did:

NOTE: I have two computer running LINUX in my home network and everything is fine. Let's call those computer: COMP1 and COMP2.


1:First I download and install Xdmx(on both comp.)
2:then I download and install TWM(on both comp.)(I did it because I've read that two instance of a gnome desktop running at the same time is not good)
3:On both computer, I change DISALLOWTCP=TRUE to DISALLOWTCP=FALSE(those entries are in my /etc/gdm/gdm.conf)
4:I reboot both COMP. to login in TWM instead of the GNOME GUI.
5:Then on both COMP. I type this in an XTERM window:

        xhost +
(Yes I open everything but I don't care since I have no security problem to think about)

6:When it's done, on COMP1, in a terminal, I type:

        Xdmx :1 -display (COMP1 IP):0 -display (COMP2 IP):0 +xinerama

The result of this is the famous gray screen of X-server(Well I've read it is from there).

I've tried several stuff but with no success. I need help with this one. 

HO! I know my english is not perfect so don't tell me. I'm working hard on it!

Maybe I should Change my distro...

Thanks!

KIPIP

---

### Post by MrHippocampus on 2008-08-04
Have you read the IBM article on getting Xdmx to work? Listing 2 shows how to start twm when you start xdmx. The following *should* work for you.

```
startx `which twm` -- `which Xdmx` :1 -display (COMP1 IP):0 -display (COMP2 IP):0 +xinerama
```

[IBM article]("http://www.ibm.com/developerworks/linux/library/os-mltihed/index.html")

Note that it would actually be ok to run gnome on Xdmx as only one copy of gnome is running. Although you would have to login to another more simple window manager for the initial logins on both machines. You might also want to try a window manager like openbox as its a bit nicer to use than twm but still lightweight.

---

