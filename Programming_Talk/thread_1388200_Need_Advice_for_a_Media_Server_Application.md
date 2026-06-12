---
title: "Need Advice for a Media Server Application"
date: 2010-01-22
forum: Programming Talk
---

### Post by megahost on 2010-01-22
So here's the story. I want to create a media server, that is connected to the surround sound system in my house. I want it so that it works as a DJ system, where each song request is sent, and the user can't send a new request until their first song is over. People will request by computer, or anything with internet access (this includes iPods). So basically, there will be a local server, where it will be running a Apache, which will host the interface which the users will type in song requests by. Using a Boolean operator system with PHP, it will find similar song names, and play the closest one to the request. The way you connect is by server locals IP.(192...). So the server will run on LAN, and will be web server based.

So here's the game plan. 
I run this on a server rack, the problem is getting the music to play through the system itself, especially supporting the fact that I was thinking about doing it on Ubuntu server. Is there any way I can do this without a graphical environment? Number 2 question would be, I understand getting a PHP function to talk to the server itself, to que the song for play will be difficult. What language should I know, to create the DJ application that hopefully will run without a Graphical interface? (I'm a web developer, hoping to learn a little more Unix programming, so this is my project for that.) I usually find fun in learning other programming languages, as long as what I'm learning will be useful. So what language should I create this application in? From there, how would I get the PHP file to tell the computer what to run?

Your input is much appreciated

---

### Post by denarced on 2010-01-22
Sounds to me like you'll need something like mpd (music-player-daemon). Usually it is used through a GUI and there are several so there propably is a text based too or some other solution.

---

### Post by megahost on 2010-01-22
Thanks! How can I tie that with a web page to request music

---

### Post by Hellkeepa on 2010-01-23
HELLo!

You'll need to have the PHP script call the MPD via the command line, with the correct parameters. Remember to use the correct escaping commands, before adding the stuff to the command.

Happy syncin'!

---

### Post by megahost on 2010-01-23
> **Hellkeepa said:**
> HELLo!

You'll need to have the PHP script call the MPD via the command line, with the correct parameters. Remember to use the correct escaping commands, before adding the stuff to the command.

Happy syncin'!

Thanks ALOT! Wish me luck on my project.

---

### Post by Can+~ on 2010-01-23
> **megahost said:**
> the user can't send a new request until their first song is over. People will request by computer, or anything with internet access (this includes iPods)

Let me stop you right there. Instead of that, why not the users form a queue of song requests? Having to constantly stand up to select the next song sounds annoying.

> **megahost said:**
> Using a Boolean operator system with PHP, it will find similar song names, and play the closest one to the request.

Not sure what you mean with that? A similar song can't be deducted with boolean algebra, like "song1 == song2" doesn't mean anything.

Current song-similarity engines are based on human perception. Meaning that users (like in grooveshark) propose songs to be similar to other songs (For instance, if you heard a song X that you liked, and then you said that you liked song Y, then probably other users may find that connection too). This forms a directed, weighted graph. And choosing the next song is based off probabilities. Is this what you mean?

> **megahost said:**
> Is there any way I can do this without a graphical environment?

Sure. In fact, you may find the job already done, there are song players that are console-only in linux, and there are also utilities that can play music.

> **megahost said:**
> Number 2 question would be, I understand getting a PHP function to talk to the server itself, to que the song for play will be difficult.

I don't think that's difficult at all. The simplest way would be to do something like a system call, or dispatch it to another application, or feed a daemon. A daemon seems reasonable, I would go with that route:

[Music Playing Daemon]("http://www.linux.com/archive/articles/62248")
[XMMS2]("http://librenix.com/?inode=10246")


> **megahost said:**
> I usually find fun in learning other programming languages, as long as what I'm learning will be useful. So what language should I create this application in? From there, how would I get the PHP file to tell the computer what to run?

I don't like much PHP, but it surely can do the job.

---

### Post by megahost on 2010-01-23
> **Can+~ said:**
> Let me stop you right there. Instead of that, why not the users form a queue of song requests? Having to constantly stand up to select the next song sounds annoying.



Not sure what you mean with that? A similar song can't be deducted with boolean algebra, like "song1 == song2" doesn't mean anything.

Current song-similarity engines are based on human perception. Meaning that users (like in grooveshark) propose songs to be similar to other songs (For instance, if you heard a song X that you liked, and then you said that you liked song Y, then probably other users may find that connection too). This forms a directed, weighted graph. And choosing the next song is based off probabilities. Is this what you mean?



The reason why I have the single request system before a song is over, is because maybe someone might try and fill up the requests with ridiculous or inappropriate songs. The system can be moderated, but a single request system to start will make my job easier. So basically, it's one algorithm problem. If no songs are selected, it will shuffle the library of currently stored songs. 

What I mean when I said boolean operators, is that if the server can't find that exact song name, it will find the closest to similar song. By finding the closest to similar song, it uses similar characters. Which also will include a similar artist find.

---

