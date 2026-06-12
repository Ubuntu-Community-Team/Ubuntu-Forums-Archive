---
title: "html embedded player question"
date: 2007-02-24
forum: Programming Talk
---

### Post by paydaydaddy on 2007-02-24
This is probably a very simple question for this forum, but I haven't been able to find the answer elsewhere, so here goes. How do I write a tag that will load a simple player in Firefox. I have a myspace page that I set up to play one of my original songs upon load. It works fine with IE but not with firefox. I will post the code and URL to the page below and perhaps some knowledgeable person will have the answer. With firefox I can go directly to the site where the file is stored, click on the link and it streams using mplayer. It just won't start or load a player console when the page loads.

code:
 <object type="application/x-mplayer2" classid="6BF52A52-394A-11d3-B153-00C04F79FAA6" height="45" width="280">
  <param name="fileName" value="http://www.mediamax.com/paydaydaddy/Hosted/scotty.mp3" />
  <param name="URL" value="http://www.mediamax.com/paydaydaddy/Hosted/scotty.mp3" />
  <param name="src" value="http://www.mediamax.com/paydaydaddy/Hosted/scotty.mp3" />
  <param name="allownetworking" value="internal" />
  <param name="allowScriptAccess" value="never" />
  <param name="enableJSURL" value="false" />
  <param name="enableHREF" value="false" />
  <param name="saveEmbedTags" value="true" />
</object>

URL:[http://www.myspace.com/texanmccabe](http://www.myspace.com/texanmccabe)

Your knowledgeable input appreciated.:guitar:

---

### Post by paydaydaddy on 2007-02-24
A few people have looked. Nobody has answered. Is this posted in the wrong sub-forum? Where would you suggest that I look for the answer. I have done some googling but have failed to come up with the solution. Anybody?

---

### Post by Mirrorball on 2007-02-24
Not an answer to your question, but I really think you should leave it the way it is. Music in websites is annoying, because sometimes I'm already listening to a song and I don't want it interrupted.

---

### Post by paydaydaddy on 2007-02-24
In general I agree with your opinion on music in webpages. The exception is when music is expected. The main reason that I want the page to load with a player console is to give the viewer control over what they hear. Also this is a somewhat academic question that arises because I haven't been able to make the page/player appear as I want. The desired knowledge is much more "how and why" than "must implement". Ya see what I mean?

---

### Post by Mirrorball on 2007-02-24
> **paydaydaddy said:**
> The exception is when music is expected.
And why would music be expected on your page?

---

### Post by paydaydaddy on 2007-02-24
First of all most of the myspace pages that I have visited do have music that plays when the page opens. I suppose that those posting are of the opinion that it is representative of their personality. Just a guess. Secondly, the majority of people who visit my page know me and know that I am a musician and would probably be surprised if I didn't have one of my songs playing. I don't get a lot of traffic from people lookin' to hook up. Know what I mean?

---

