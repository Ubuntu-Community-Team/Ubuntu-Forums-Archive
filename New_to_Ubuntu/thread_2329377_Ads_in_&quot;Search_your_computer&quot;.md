---
title: "Ads in &quot;Search your computer&quot;"
date: 2016-06-30
forum: New to Ubuntu
---

### Post by Pinkie_B on 2016-06-30
Hi Ubuntu-ers,

I'm sort of new to ubuntu, but very new to the forums. In the latest install of ubuntu I noticed that if you hit the windows key on the keyboard, or click the icon in the corner of the taskbar you can search your computer very much like the spotlight search in mac. This is an awesome feature.

However, in searching for my computer, the results are showing advertisements from the web. Most recently I searched "firefox" because that's how I open my browser and below the files on my computer were a list of links to items with price tags. 

This pisses me off incredibly and I want to make it go away before I throw my computer out the window in a fit of rage. 


...so, does anyone know how I can make the "search your computer" command search only my computer?

Thanks

---

### Post by yancek on 2016-06-30
System Settings, Privacy, Search results tab.

---

### Post by X-RED_Tech on 2016-06-30
Isn't the online search disabled by default now?

[EDIT]

I really couldn't remember the last time I had it so I activated just to see what would happen.
Typed "firefox" but couldn't see much additional info/suggestions: Firefox OS, Wikipedia entries and more scopes. Yes, I had the Amazon one as well as all the other defaults scopes active but I didn't show any products with price tags.

Now...
When I searched "hot girl" WOW \\:D/ 
I bow to you, online dash search...

---

### Post by Pinkie_B on 2016-07-04
Is this the settings window you were referring to? 
It seems to have worked. 

...that said, maybe I'm imagining it, but I thought there were more customizable options? Or perhaps I'm confused which operating system I was using...

Anyway, thank you. No ads are incredibly stress relieving.

---

### Post by CantankRus on 2016-07-04
You can choose what recent documents are shown in the dash
and exclude applications in the "Files and Applications" tab.

You can also unclutter the dash by removing scopes you don't use.
Terminal command to show current scopes...
```
gsettings **get** com.canonical.Unity.Dash scopes
```
eg
```
**[COLOR="#008000"]glen@Xenial:~$[/COLOR] gsettings get com.canonical.Unity.Dash scopes**
['home.scope', 'applications.scope', 'files.scope', 'video.scope', 'music.scope', 'photos.scope', 'social.scope']
```
Note the format... scopes are enclosed in single quotes followed by a comma and space.

I only want to see the home, applications and files scopes so I use....
```
gsettings **set** com.canonical.Unity.Dash scopes "['home.scope', 'applications.scope', 'files.scope']" 
```
You will need to logout/in to see the changes.

To reset back to default use...
```
gsettings **reset** com.canonical.Unity.Dash scopes
```

---

### Post by wildmanne39 on 2016-07-06
Please use thumbnails or Url's when posting images because many people have slow internet connections and loading pages with large images is very difficult for them.

---

