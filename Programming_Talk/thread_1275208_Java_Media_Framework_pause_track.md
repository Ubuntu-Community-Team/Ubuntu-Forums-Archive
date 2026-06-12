---
title: "Java Media Framework pause track"
date: 2009-09-25
forum: Programming Talk
---

### Post by tashe on 2009-09-25
Hi
I am trying to make my own mp3 player with the Java Media Framework. So far I've managed to make a Swing program that has a playlist and play and stop buttons.
Next thing that I want to do is implement a Pause button. I've searched the API and it doesn't tell how can this be done. For the start and stop there are already made methods from the API that I invoke. But nothing similar for Pause.
If anyone has an idea how to solve this I'd be very thankful because its annoying to get stuck on such a trivial problem.

I am using the Player class. This is how I obtain the player.

```

Player p = Manager.createRealizedPlayer(new File("test.mp3").toURI().toURL());
p.start();

```

Thanks

---

### Post by PaulM1985 on 2009-09-27
Hi

I am not overly familiar with Media Framework but have you looked into the functions getMediaTime() and setMediaTime() in the Player class?

When the user clicks on the pause button you could get the media time and stop() the player.  When the user unpauses you could set the media time to the time recorded from when the pause button was pressed and use the start() method.

Having said all that, I looked into the start() method and it seems to play from where it was last stopped.

From the API about start():
Starts the Player as soon as possible. If the Player was previously stopped by calling stop or reaching a preset stop time, it will resume playback from where it was previously stopped. If the Player has reached the end of media, calling start will automatically start the playback from the start of the media. 


So this seems that all you need to do is stop the player and start it again and it should start from where you stopped it.

Hope some of this helps.

Paul

---

