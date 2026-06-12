---
title: "html/flash help with backgrounds"
date: 2007-04-21
forum: Programming Talk
---

### Post by toosweetnitemare on 2007-04-21
i know this question isnt entirely related to Ubuntu, but i was wondering if anyone knows flash since i seem to be stuck on a problem and the forums' never let me down before.
my problem is that i can not change a background color to a background image. simple as that but i just cant seem to do it. here is the code im using...

> 

<center><object enableJSURL="false" enableHREF="false" saveEmbedTags="true" allowScriptAccess="always" allownetworking="internal" 

type="application/x-shockwave-flash" allowScriptAccess="always" allownetworking="internal" height="185" width="242" 

data="http://lads.myspace.com/music/musicplayer.swf?n=aHR0cDovL211c2ljLm15c3BhY2UuY29t&t=mmuwDG8HgK7nKz7z4oKrN+mq/5IbwOvuTxmsspCIlNLEwRAZ49UIvQjGhCYp80fUqsvbg

3CmW5jyuYe8ScOL2A==&u=NTA1OTYyNjM=&a=0&d=NzkyNTI0NDNeMTE3MTA0MjUyOA==&p=aHR0cDovL2lwcm9maWxlLm15c3BhY2UuY29tL2NvbW1hbmQuYXNweD9pZmlkPU1HTUdDaXNHQVFRQmdqZFlBND

JnVlRCVEJnb3JCZ0VFQVlJM1dBTUJvRVV3UXdJREFnQUJBZ0ptQXdJQ0FNQUVDQ2Z3OW1zbGhwcDhCQkRxdlY3VXNpNVlyajdDbUh4RU4vaDRCQmdjRmU1MG5adWVaelUyaE5penB0Yk5EeUt6N0Jmd0JrQT0=

">
  <param name="allowScriptAccess" value="always" />
  <param name="allowNetworking" value="all" />
  <param name="movie" 

value="http://lads.myspace.com/music/musicplayer.swf?n=aHR0cDovL211c2ljLm15c3BhY2UuY29t&t=mmuwDG8HgK7nKz7z4oKrN+mq/5IbwOvuTxmsspCIlNLEwRAZ49UIvQjGhCYp80fUqsvb

g3CmW5jyuYe8ScOL2A==&u=NTA1OTYyNjM=&a=0&d=NzkyNTI0NDNeMTE3MTA0MjUyOA==&p=aHR0cDovL2lwcm9maWxlLm15c3BhY2UuY29tL2NvbW1hbmQuYXNweD9pZmlkPU1HTUdDaXNHQVFRQmdqZFlBN

DJnVlRCVEJnb3JCZ0VFQVlJM1dBTUJvRVV3UXdJREFnQUJBZ0ptQXdJQ0FNQUVDQ2Z3OW1zbGhwcDhCQkRxdlY3VXNpNVlyajdDbUh4RU4vaDRCQmdjRmU1MG5adWVaelUyaE5penB0Yk5EeUt6N0Jmd0JrQT0

=" />
  <param name="quality" value="high" />
  <param name="bgcolor" value="http://a49.ac-images.myspacecdn.com/images01/55/l_bda4cc41adea6dcfd20caf0b9465bf98.gif" />
</object></a>




---

### Post by barmazal on 2007-04-21
I have no idea what you mean and your code seems uncorrect or at least not pasted right.

If you want to change background of Flash movie, do it via Flash itself. You can pass parameter with background code to Flash movie but i wouldn't advice that.
If you want a background of HTML behind the movie then change it via HTML by giving style to element holds the Object tag. Like put your object into <div style="background-color:#000"> OBJECT </div> or you can give layer a class or id and insert all functionality via CSS file which is more semantic (correct) web desgin.

Again i don't know what you mean exactly.

---

### Post by toosweetnitemare on 2007-04-21
its a music player. if you had run that in an explorer window it would be a media player. where i have the background image, if you change that to a color the color behind the song title changes. i just wanted it to be an image instead of a color. Thank you for your help

---

### Post by barmazal on 2007-04-21
<div style="background-image:url('PUTURLHERE')">OBJECT</div>

---

### Post by toosweetnitemare on 2007-04-21
<div style="background-image:url('http://a49.ac-images.myspacecdn.com/images01/55/l_bda4cc41adea6dcfd20caf0b9465bf98.gif')">OBJECT</div>

it doesnt seem to work.

---

### Post by barmazal on 2007-04-22
did you put object inside coz without something inside div will be sized to 0px width 0px height, if you want to insure it exact the size of animation, then just enter 

<div style="background-image:url('PUTURLHERE');width:XXXpx;height:XXXpx">OBJECT</div>

---

### Post by toosweetnitemare on 2007-04-22
thanks! ive tried messing with the code a few times the closest ive gotten is to this:
> <div style="background-image:url('http://a734.ac-images.myspacecdn.com/images01/36/l_28d523da08544cf5b5a424587f9b7e9d.gif')"><center><object enableJSURL="false" enableHREF="false" saveEmbedTags="true" allowScriptAccess="never" allownetworking="internal" type="application/x-shockwave-flash" allowScriptAccess="never" allownetworking="internal" height="185" width="242" data="http://lads.myspace.com/music/musicplayer.swf?n=aHR0cDovL211c2ljLm15c3BhY2UuY29t&t=mmuwDG8HgK7nKz7z4oKrN+mq/5IbwOvuTxmsspCIlNLEwRAZ49UIvQjGhCYp80fUqsvbg3CmW5jyuYe8ScOL2A==&u=NTA1OTYyNjM=&a=0&d=NzkyNTI0NDNeMTE3MTA0MjUyOA==&p=aHR0cDovL2lwcm9maWxlLm15c3BhY2UuY29tL2NvbW1hbmQuYXNweD9pZmlkPU1HTUdDaXNHQVFRQmdqZFlBNDJnVlRCVEJnb3JCZ0VFQVlJM1dBTUJvRVV3UXdJREFnQUJBZ0ptQXdJQ0FNQUVDQ2Z3OW1zbGhwcDhCQkRxdlY3VXNpNVlyajdDbUh4RU4vaDRCQmdjRmU1MG5adWVaelUyaE5penB0Yk5EeUt6N0Jmd0JrQT0=">
  <param name="allowScriptAccess" value="never" />
  <param name="allowNetworking" value="all" />
  <param name="movie" value="http://lads.myspace.com/music/musicplayer.swf?n=aHR0cDovL211c2ljLm15c3BhY2UuY29t&t=mmuwDG8HgK7nKz7z4oKrN+mq/5IbwOvuTxmsspCIlNLEwRAZ49UIvQjGhCYp80fUqsvbg3CmW5jyuYe8ScOL2A==&u=NTA1OTYyNjM=&a=0&d=NzkyNTI0NDNeMTE3MTA0MjUyOA==&p=aHR0cDovL2lwcm9maWxlLm15c3BhY2UuY29tL2NvbW1hbmQuYXNweD9pZmlkPU1HTUdDaXNHQVFRQmdqZFlBNDJnVlRCVEJnb3JCZ0VFQVlJM1dBTUJvRVV3UXdJREFnQUJBZ0ptQXdJQ0FNQUVDQ2Z3OW1zbGhwcDhCQkRxdlY3VXNpNVlyajdDbUh4RU4vaDRCQmdjRmU1MG5adWVaelUyaE5penB0Yk5EeUt6N0Jmd0JrQT0=" />
  <param name="quality" value="high" />
  <param name="bgcolor" value="000000" />
</object></a></div>

that gives the image to the back ground of the window, i need it behind the music titles in the lower right hand corner of the flash.

---

### Post by barmazal on 2007-04-22
just a question why do you have closing anchor and no opening and what role anchor plays in whole the issue?

Other thing, i couldn't understand what you trying to achieve but it seems you have mp3 player which you want to be transparent so you can see the girl picture below?

---

### Post by toosweetnitemare on 2007-04-22
this is a player from myspace. thats how i got the code, im on a streetteam for the band and i took the player code straight from their myspace. all i know is what i get to see. if you want to look at the code yourself, the website address is  
[http://www.myspace.com/marymagdalan](http://www.myspace.com/marymagdalan)  

Thanks again for all your help, cause im not sure what exactly in doing here, i know xhtml and css2 but this code just doesnt want to do what i want it to.

---

### Post by barmazal on 2007-04-22
well, i don't know how mySpace applies the code and whether you can modify it on that level.

My advice, messed up myspace doesn't give much. Made me close it right away. Ive seen her face, heard her singing thats all for me. Rest should be on her website where you can have any type of code you want as she wants it, ads all local and well organized. Even punks need it.

Advice her, i would force my client though.

---

