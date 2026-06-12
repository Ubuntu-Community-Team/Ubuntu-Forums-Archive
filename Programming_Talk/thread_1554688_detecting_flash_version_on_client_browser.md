---
title: "detecting flash version on client browser"
date: 2010-08-17
forum: Programming Talk
---

### Post by jamesbon on 2010-08-17
I am using a simple javascript to connect my flv streams with Red5 (streaming server) every thing is working perfectly fine in Mozilla and Chrome.
But when it comes to IE it simply wont load the player.
Here is my script
```

<object id="single1" classid="clsid:D27CDB6E-AE6D-11cf-96B8-444553540000" height="290" width="360" name="single1"> 
<param name="movie" value="[http://domain2/player.swf](http://domain2/player.swf)"> 
<param name="allowfullscreen" value="true"> 
<param name="allowscriptaccess" value="always"> 
<param name="wmode" value="transparent"> 
<param name="flashvars" 
value="file=/directory/video.flv&amp;streamer=rtmp://domain_in_question/oflaDemo"> 
<embed height="290" width="360" flashvars="file=/directory/video.flv&amp;streamer=rtmp://domain_in_question/oflaDemo" wmode="transparent" allowfullscreen="true" allowscriptaccess="always" bgcolor="undefined" 
src="[http://domain2/player.swf](http://domain2/player.swf)" name="single2" id="single2" type="application/x-shockwave-flash"></embed> 
</object>

```
How do I detect the client browser and redirect him to adobe flash upgrade page if the client browser does not have a supported 
player?

---

