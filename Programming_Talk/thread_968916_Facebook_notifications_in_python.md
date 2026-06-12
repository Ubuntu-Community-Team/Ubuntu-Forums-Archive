---
title: "Facebook notifications in python"
date: 2008-11-03
forum: Programming Talk
---

### Post by G|N| on 2008-11-03
Hello,

Does anybody know if there is a library for python available that shows me if there are new notifications for my facebook account?

It has to show me if there are new friends requests, event requests,....

Thanks

---

### Post by ad_267 on 2008-11-03
Maybe something like this: [http://wiki.developers.facebook.com/index.php/Python](http://wiki.developers.facebook.com/index.php/Python)

---

### Post by G|N| on 2008-11-03
> **ad_267 said:**
> Maybe something like this: [http://wiki.developers.facebook.com/index.php/Python](http://wiki.developers.facebook.com/index.php/Python)

It seems that this can only be used if you are creating a facebook application. I only want a notifier from my main facebook page.

[http://wiki.developers.facebook.com/index.php/Notifications.get](http://wiki.developers.facebook.com/index.php/Notifications.get)
This is what i need but from the documentation I have to pass an api_key and a sig. I have no idea how to get these from facebook.

api_key: The vendor-specific API key corresponding to the site making the API call. This is the same as in the login request.

---

### Post by ruckerz on 2009-02-02
I don't think it's possible to register a listener or callback with facebook to have them contact you if you have a new notification (outside of email). So you can either watch your emailk or you can write a python FB app that periodically queries facebook and sees if there's any changes from the last query.

---

### Post by Montblanc_Kupo on 2009-02-02
> **ruckerz said:**
> I don't think it's possible to register a listener or callback with facebook to have them contact you if you have a new notification (outside of email). 

Well... depends what is needed.

Pidgin has a plugin for facebook. Allows you to see and chat with users using the facebook chat system. It also makes all your notifications show up as pidgin notifications. So any notification tags you have set would control it.

Even if you didn't want to use pidgin for this... it does show that it's possible.

Here's the link to the plugin. Heck, might even be able to just take it apart to see how they did it.

[http://code.google.com/p/pidgin-facebookchat/](http://code.google.com/p/pidgin-facebookchat/)

---

### Post by ruckerz on 2009-02-02
> **Montblanc_Kupo said:**
> Well... depends what is needed.

Pidgin has a plugin for facebook. Allows you to see and chat with users using the facebook chat system. It also makes all your notifications show up as pidgin notifications. So any notification tags you have set would control it.

Even if you didn't want to use pidgin for this... it does show that it's possible.

But the question would be.. 

Is Pidgin receiving messages from facebook by acting as a listener?  I'd love to be aware of something in the FB API that allows you to register listeners. 

or does Pidgin periodically poll facebook?

---

### Post by Montblanc_Kupo on 2009-02-02
> **ruckerz said:**
> But the question would be.. 

Is Pidgin receiving messages from facebook by acting as a listener?  I'd love to be aware of something in the FB API that allows you to register listeners. 

or does Pidgin periodically poll facebook?

No idea. I couldn't program My way out of a wet paper bag. But from a usability standpoint... what difference does it make? :)

I see My friends sign on and off... if I have the page open when I'm chatting... I see the text mirrored between the website chat and the pidgin chat... notifications show up instantly as notifications in pidgin... *shrug*

I don't know if it's polling or listening... but it works... which is why I said it depends on what is needed. If the OP simply wants to get their FB notifications without logging in... there ya go. If there is some underlying programming that is going on... well... I can't help beyond just pointing out that I'd seen and used the plugin.

---

### Post by ruckerz on 2009-02-02
> **Montblanc_Kupo said:**
> No idea. I couldn't program My way out of a wet paper bag. But from a usability standpoint... what difference does it make? :)

I see My friends sign on and off... if I have the page open when I'm chatting... I see the text mirrored between the website chat and the pidgin chat... notifications show up instantly as notifications in pidgin... *shrug*

I don't know if it's polling or listening... but it works... which is why I said it depends on what is needed. If the OP simply wants to get their FB notifications without logging in... there ya go. If there is some underlying programming that is going on... well... I can't help beyond just pointing out that I'd seen and used the plugin.

Point taken. It seems that the Facebook Chat API is a little more interesting. 

For those interested.here's a discussion..
[http://coderrr.wordpress.com/2008/05/06/facebook-chat-api/](http://coderrr.wordpress.com/2008/05/06/facebook-chat-api/)
[http://andrew-hite.com/blog/2008/06/the-hidden-facebook-chat-api/](http://andrew-hite.com/blog/2008/06/the-hidden-facebook-chat-api/)

The second notes that it's a 'hidden' api. Looks like Pidgin got to it :)
Cheers

---

### Post by BRUUUCE on 2009-02-02
i dont know if this is against FB TOS, but, check out pythons http lib? And have script login every five minutes and check for you.

---

### Post by G|N| on 2009-02-02
I got the script working and it is included in the new specto 0.3 rc1 version.

It notifies the user for new wall posts, messages, notifications and requests and it works very good!

---

### Post by crinus on 2011-12-04
I'm also looking for command line tools for checking the FB
account. 

If there's progress in here, would be cool to hear it out. 

I use a lot of shell stuff, and sometimes on a constricted network link, like currently. I like to minimize network bytes if possible. 
Sometimes just a notification is all I need.

---

