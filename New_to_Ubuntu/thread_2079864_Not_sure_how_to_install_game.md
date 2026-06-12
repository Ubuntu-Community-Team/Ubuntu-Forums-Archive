---
title: "Not sure how to install game"
date: 2012-11-02
forum: New to Ubuntu
---

### Post by Luckyjfl on 2012-11-02
Hi Guys, complete Linux Noob here. I downloaded a nice game I would love to play, but have not got the faintest idea how to install it on Ubuntu. I open all the files related to the game, but do not seem to be able to find a Install file.
I would appreciate a bit of help please.  I guess I have to use the command but do not know the correct way to do this.  The game is Just Cause 11.

Thank you for any help.

Luckyjfl

:)

---

### Post by squakie on 2012-11-02
I'm not a gamer, so forgive me , but is it a Windows program or a native linux program?

---

### Post by monstara on 2012-11-02
I've played it, it's a Windoze game. You probably won't be able to play it, sorry... 
You could try using Wine. Install it from the Software Center and then in a terminal navigate to the directory where the game is:
```
cd /home/username/Games/justcause
```where username should be your login name.
Then in the terminal type:
```
wine justcause.exe
```where you should replace the correct .exe name

---

### Post by squakie on 2012-11-03
Another option, but not free, was pointed out to me by user lkaemer on Friday and was a "miracle" for me : CodeWeavers Crossover.  I had some Windows programs I really needed to use that just wouldn't run in Wine on it's own, but work great with Crossover.  I have a couple of very product specific path things to work out on a couple of games (actually for my Dad - I wanted them working first).  You can download the demo version and try it free for 15 days, so you may want to try that.  I think I paid something like $39.99 or something for the cheapest way to get a license.

---

### Post by squakie on 2012-11-03
> **monstara said:**
> I've played it, it's a Windoze game. You probably won't be able to play it, sorry... 
You could try using Wine. Install it from the Software Center and then in a terminal navigate to the directory where the game is:
```
cd /home/username/Games/justcause
```where username should be your login name.
Then in the terminal type:
```
wine justcause.exe
```where you should replace the correct .exe name

It's quite possible this has changed, but it has always been that the path to an executable in Wine was going to be /home/<userid>/.wine in the drive-c folder.  This is where it keeps Windows executables, etc., on a virtual disk.

---

