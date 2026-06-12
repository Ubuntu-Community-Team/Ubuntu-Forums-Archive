---
title: "Setting default video player to VLC doesn't work"
date: 2011-10-08
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by alphacrucis2 on 2011-10-08
I tried setting default video application under system settings - system info - default applications to vlc. However nautilus doesn't obey this change. I'm wondering if it is similar to the issue with setting the default browser discussed in another thread.

---

### Post by andrewabc on 2011-10-08
With older ubuntu versions, you had to right click on video file and select VLC as player for that filetype, and it would remember it for that filetype (so do it for all your common video filetypes that you come across).

---

### Post by Utew on 2011-10-08
Yeah, I'm seeing this same issue... even right clicking a video file and removing all other choices (except the one I want), doesn't seem to hold it's setting. 

Same issue trying to set a different default with System Settings > System Info > Default Applications. Though curiously I am able to set  different defaults for all other classes of apps (in System Info), just not videos. Even changing the default browser  works fine for me.

---

### Post by alphacrucis2 on 2011-10-08
> **andrewabc said:**
> With older ubuntu versions, you had to right click on video file and select VLC as player for that filetype, and it would remember it for that filetype (so do it for all your common video filetypes that you come across).

You can select vlc from the nautilus context menu but there is no option to remember the selection in Oneiric.

---

### Post by mc4man on 2011-10-08
Nothings really changed, you need to set vlc once on a per mimetype just as before. screen ex. on quicktime (.mov ), highlighting vlc & then clicking on 'Set as default' will do the deed.

What the System Setting video option is for don't know, seems worthless as "video" is quite generic & also has no apparent effect on any local file

If you change the Music player option in System Settings then that will have the grand effect of switching what is shown in the main dash window for "Listen to Music"

---

### Post by alphacrucis2 on 2011-10-08
> **mc4man said:**
> Nothings really changed, you need to set vlc once on a per mimetype just as before. screen ex. on quicktime (.mov ), highlighting vlc & then clicking on 'Set as default' will do the deed.

What the System Setting video option is for don't know, seems worthless as "video" is quite generic & also has no apparent effect on any local file

If you change the Music player option in System Settings then that will have the grand effect of switching what is shown in the main dash window for "Listen to Music"

Yes setting vlc as default that way does work. Maybe I should bug the system setting video function. I guess it depends on what it is actually intended to do.

---

### Post by mc4man on 2011-10-08
> **alphacrucis2 said:**
>  I guess it depends on what it is _actually intended to do_.

That is the question - user set  associations that differ from the 'delivered' defaults are handled in ~/.local/share/applications/mimeapps.list on a per type basis

But - on a default install totem is the default for most video formats, changing thru the SS option does nothing

If however you remove totem then banshee becomes the general default video player, if you additionally  remove banshee then vlc may become the new default player - does so here.

So it seems that the 'default' video player is set from a sort of 'fallback' list - if A is installed it's the default
If A isn't installed then B is the default, if A/B aren't installed then C, ect.
There was/is some code in unity that did this but not sure if that's what's in play here...

---

### Post by Harry33 on 2011-10-09
You change the default applications

for a given user:
 .local/share/applications/mime

for systen-wide:
 /usr/share/applications/mimeinfo.cache

for gnome:
 /etc/gnome/defaults.list

---

### Post by Harry33 on 2011-10-09
System-wide settings for default applications are set by the package
- desktop-file-utils

---

### Post by seeker5528 on 2011-10-10
> **alphacrucis2 said:**
> I tried setting default video application under system settings - system info - default applications to vlc.

Looks like Nautilus is either hardcoded and doesn't look for the user selected default, or looks in the wrong place for user selected defaults and when it doesn't find them falls back to some defined elsewhere, maybe hardcoded set of applications.

On the bright side, I see that the dash does the right thing for music and email, looks like 'View Photos' is still hard coded to Shotwell though.

Later, Seeker

---

### Post by seeker5528 on 2011-10-10
> **Harry33 said:**
> for gnome:
/etc/gnome/defaults.list

That's the ticket.

In theory, if you copy this file to '~/.local/share/applications/', then replace the defined applications with the ones you want, it should work. The defaults.list may already exist there, it did on my system until I deleted it.



Later, Seeker

---

### Post by mc4man on 2011-10-10
> **seeker5528 said:**
> That's the ticket.

In theory, if you copy this file to '~/.local/share/applications/', then replace the defined applications with the ones you want, it should work. The defaults.list may already exist there, it did on my system until I deleted it.

Later, Seeker
If you're going to do that might as well use ~/.local/share/applications/mimeapps.list, it will trump any defaults.list for same types anyway. (still is a type by type editing or creating method

I think the real question of thread is why doesn't changing the default in g-c-c for video (& music is the same), change anything or change anything in manner  that users are expecting.

---

### Post by seeker5528 on 2011-10-12
> **mc4man said:**
> If you're going to do that might as well use ~/.local/share/applications/mimeapps.list, it will trump any defaults.list for same types anyway. (still is a type by type editing or creating method

I think the real question of thread is why doesn't changing the default in g-c-c for video (& music is the same), change anything or change anything in manner  that users are expecting.

Ahhh crap!!!! Judging by the contents of that file.

It looks like setting the default audio and video through the hidden default applications dialog only sets the association for these:

audio/x-vorbis+ogg=vlc.desktop
video/x-ogm+ogg=vlc.desktop

Hang on changing....... Yep....

audio/x-vorbis+ogg=kde4-amarok.desktop
video/x-ogm+ogg=totem.desktop

Seems like a pretty significant 'WTF?!?!?!?' to me. :P

Apparently Nautilus sets it's stuff there too. Just changed the default in Nautilus by right clicking an mp3 file and setting the default from the properties window and got this....

audio/mpeg=qmmp.desktop

Apparently limited in the same way as the 'Open With' dialog', in the sense that you can't specify an application, only a .desktop file.

Hopefully 'Open With' in Nautilus will get fixed at some point so you can specify a file and it will create the appropriate mimetype.desktop file for the association.

Later, Seeker

---

