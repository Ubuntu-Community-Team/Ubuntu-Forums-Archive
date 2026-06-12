---
title: "px-500 Sprint evdo"
date: 2007-07-06
forum: Programming Talk
---

### Post by bradleyd on 2007-07-06
Hello everyone,

I recently got the px-500 pcmcia card for EVDO network from Sprint. I searched around to find setup instructions and found a couple of websites like [http://http://www.evdoforums.com/thread3813.html]("http://http://www.evdoforums.com/thread3813.html")
What I did not find was any gui connection software like they have for Windows. I had a day of down time so I put together a little gui that automates the connection process for these cards. Nothing fancy, but it works. 
 The code is not complete, there is very little error checking. I am sure there are easier and better ways to do this( am sure someone will point that out to me. LOL). I wanted to refine it more but I have to start another project so I am out of time. I hope someone will take the code and refine or even rewrite it, to make it more functional. With that said it must be run as root(it copys files to /etc/ppp/peers and /etc/ppp) There is no instant feedback when you hit the connect button. You can minimize the app after you hit connect or you can close it by the X. If you close it by the X you will have to run it again(as root) to hit the quit button to kill the ppp daemon. Also it assumes that you do not have any other devices named ppp0.
Take care,
Brad

---

