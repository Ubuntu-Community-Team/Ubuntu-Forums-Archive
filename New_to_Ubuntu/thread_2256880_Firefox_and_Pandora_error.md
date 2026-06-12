---
title: "Firefox and Pandora error"
date: 2014-12-15
forum: New to Ubuntu
---

### Post by Ella_Gebow on 2014-12-15
I just put Lubuntu on my little computer and everything was installed correctly, from what I can tell.  I opened Firefox and logged into my Pandora account-it let's me log in but then gives me this message 
                        "We've encountered an error.  Sorry, it's our fault.  Please click 'reload' to continue listening. 
 I did that and it did not fix the problem.  I went onto one of my other computers to see if Pandora really is having trouble but did not have that error come up (windows computers). 
 I also installed Chromium thinking perhaps I could just listen to it there but it tells me I have to have the most current Flash installed (which I do according to the list that I see under installed software) so I cannot get past that screen.
Appreciate help on this as that will be the main function of this little computer-Music.

---

### Post by Frogs Hair on 2014-12-15
Chromium uses pepperflashplugin-nonfree so that may explain the error. I use the Pithos Pandora client so I don't need to have a  browser open to listen. ```
sudo apt-get install pithos 
``` I would also install the Lubuntu restricted extras because Pandora may require more than flash to run via the browser.

---

### Post by Ella_Gebow on 2014-12-15
I found the pithos one and downloaded it.  I can play the music with it but I cannot do things like thumbs up, forward etc.  Is there another suggestion for being able to access with Firefox?
I did already install the Ubuntu restricted extras.  do I need to restart the computer for it to take effect?

Also, When in Chromium I get the "snap" error and do not know why.

---

### Post by Frogs Hair on 2014-12-15
I'm not sure what's up with Firefox because it works here . You can love or ban songs in Pithos by right clicking on the song playing and in order to skip ahead select the song you want and click the play arrow . If you are running a script blocker in FF you might have to white-list the Pandora site.I use Ghostery but it doen't cause any problems on the Pandora website site.

---

### Post by Ella_Gebow on 2014-12-15
Well, I can try to find out how to stop the script in firefox (or perhaps you can tell me) but I downloaded Chrome (vs Chromium which also would not work for Pandora) and it works fine.  I would rather use Firefox as I believe it is safer than Chrome but for now, I can use it the way I was used to using it.  Thank you for your help.

---

