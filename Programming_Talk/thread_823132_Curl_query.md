---
title: "Curl query"
date: 2008-06-08
forum: Programming Talk
---

### Post by PsychedelicReaction on 2008-06-08
I'm creating a small script to take a picture from my webcam and publish it directly to twitter through twitpic.

twitpic's api for upload pictures is:
> Fields to post in
(post data should be formatted as multipart/form-data):
- media (required) - Binary image data
- username (required) - Twitter username
- password (required) - Twitter password
- message (optional) - Message to post to twitter. The URL of the image is automatically added.

since i'm a noob, i don't know how to sendthe binary data in the curl command. someone could help me? thanx!

---

### Post by Phenax on 2008-06-09
```
--data-binary <data> HTTP POST binary data (H)
```To send an image's binary data, try
```
--data-binary "@image.png"
```Which should send the binary data of image.png

---

### Post by PsychedelicReaction on 2008-06-09
this is what i send from command line
>  curl -d "username=mikkysixx" -d "password=******" -d "message=messaggio" --data-binary "@AVATARGH.jpg" [http://twitpic.com/api/uploadAndPost](http://twitpic.com/api/uploadAndPost)

and that's what i get

> <?xml version="1.0" encoding="UTF-8"?>
<rsp stat="fail">
	<err code="1002" msg="Image not found" />
</rsp>


---

### Post by Phenax on 2008-06-09
I found this bit of code [here](http://phreadz.com/experiments/twitpic/twitpic.phps).

```
curl -F media=@/full/path/to/your/image.jpg -F username=YOUR_TWITTER_USERNAME -F password=YOUR_TWITTER_PASSWORD -F message=\"your twitter message\" http://twitpic.com/api/uploadAndPost
```

---

### Post by pradeepthundiyil on 2010-12-30
hi,

i am trying to send an image file to printer using curl. I am using curl command line tool for this and the command i used is ***curl --data-binary "@filename ip:port"***. I can take print of a text file like this,but unable to get image print.

But this doesn't work. Any help would be appreciated..

---

