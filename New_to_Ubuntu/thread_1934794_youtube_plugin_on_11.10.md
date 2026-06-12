---
title: "youtube plugin on 11.10"
date: 2012-03-02
forum: New to Ubuntu
---

### Post by itsols on 2012-03-02
I've just installed Ubuntu 11.10.

When I open a youtube video, I get the alert that a plugin needs to be installed. But within seconds the video PLAYS fine.

Then I close everything and come back to find the same alert. Then again within a few seconds it plays. I haven't installed the plugin (flash player).

So my concerns:

1. Do I really need to install the plugin? Afterall the videos play fine.

2. Why this alert when I don't need a plugin?

3. Is there a way to stop this alert?

---

### Post by wolfen69 on 2012-03-02
Install the [flash aid]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/") plugin for firefox. The messages will go away.

---

### Post by kaldor on 2012-03-02
> **itsols said:**
> 
1. Do I really need to install the plugin? Afterall the videos play fine.

2. Why this alert when I don't need a plugin?

3. Is there a way to stop this alert?

YouTube is trying to convert all of its videos to HTML5 standards, which require no plugins. This is not yet complete and the site is still largely dependent on Flash.

1) I recommend you install the ubuntu-restricted-extras package. This will give you a whole host of useful codecs, fonts, and plugins such as Flash. Search for it in the Software Centre or simply run this command:

```
sudo apt-get install ubuntu-restricted-extras
```

2) YouTube will try to fall back to HTML5 when there's no plugin detected.

3) Unsure. It'll go away if you install the ubuntu-restricted-extras package, though.

---

### Post by itsols on 2012-03-02
Thanks forlks!

I think the plug-ins are great!

---

