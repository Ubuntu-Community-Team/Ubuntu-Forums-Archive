---
title: "Simple Ruby on Rails error. Need help spotting the bug!"
date: 2009-02-14
forum: Programming Talk
---

### Post by thenetduck on 2009-02-14
Hi
I'm a little new to Ruby on Rails so I think i'm overlooking something but I am rendering a partial into a template and getting this error...

Partial --> [http://pastebin.com/m6b92a457](http://pastebin.com/m6b92a457)
Template --> [http://pastebin.com/m6b92a457](http://pastebin.com/m6b92a457)

the Error --> [http://pastebin.com/m1c702579](http://pastebin.com/m1c702579)


Does anyone know what that error means? Also, do you know how to fix it? I am a little confused. 

Thanks! 
The Net duck

** What was wrong **..
Well it looks like I was only able to give one object at a time and I was given an large array of objects. I solved this by using a 
for u in user 

type for loop instead of a 

remote_form_for(user) do |u| 

type loop. 

Hope this helps someone. :) 

The Net Duck

---

