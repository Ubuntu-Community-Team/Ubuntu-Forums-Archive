---
title: "Hosting java program on the web"
date: 2007-05-02
forum: Programming Talk
---

### Post by Bobtheknight on 2007-05-02
My betters,

I made a program using java that captures the screenshot and save it as a jpg file.  Now I want it on my webserver.  Specifically, I'm thinking of integrating it into a Flash server.  My idea is like I have a flash program that runs in a browser.  On the flash program (inside it) is a button that I press, and it calls to my java program and does something, so that the user's screen is saved as a .jpg file and it gets uploaded into the flash server and is displayed into the flash window :)

That sounds very complicated.  I hope you guys understand what I'm trying to do.  Failing that, can someone point me to something where people host java games and all we have to do is go to their url, wait for the game to load, and we get to play.  

What I'm trying to say is make it so that user don't have to download my screenshot.class manually and run it with the "java screenshot" command.

Thanks!

---

### Post by Todd Bealmear on 2007-05-02
Hmmm...sounds tricky.  You might be able to do it with an applet, but I don't know enough about applets to actually tell you any more.

---

### Post by Bobtheknight on 2007-05-03
Hey thanks for your reply.  Here is what I am thinking of doing:

1.  Java applet take screenshot.
2.  Make remote procedure call to ColdFusion server (server is already up) to write the BufferedImage object as jpg on the server
3.  When RPC returns, tell Flash running off the server file is ready.
4.  Flash displays the file.

I'm now at step 2, how do I make a remote procedure call to ColdFusion?

---

