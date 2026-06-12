---
title: "wxPython Stock Icons"
date: 2010-04-28
forum: Programming Talk
---

### Post by turvyc on 2010-04-28
Hi all,

I'm working on a Python application using the wonderful GUI toolkit that is wxPython, because it's my goal to have it work on Linux, Mac AND Windows.

Now, according to the wxPython style guidelines, the preferred method of referring to buttons, menu items, etc. is by using the stock wxPython id (like, wx.ID_SAVE), as this will load both the system default text and icon for the action, giving the program a nice native look and feel.

Now, I'd like to do the same for the toolbar of the program, but the default tools use different IDs (like, wx.TB_FILE_SAVE). Maybe no big deal, but the default toolbar icons are rather lacking. Namely, while a default ID exists for a print preview button/menu item (wx.ID_PREVIEW), there is no such default ID for the toolbar! 

My question is, how can I get the default icons which are recognized by wxPython into the toolbar? I've tried mucking around with ArtProvider a whole bunch but to no avail. I know that wxPython must be able to access the icons, but how can I "transfer" a default button/menu item ID to a default Toolbar ID?

Thanks so much!

---

### Post by robots.jpg on 2010-04-28
Hopefully I'm not misunderstanding the problem, but using wx.ArtProvider to grab the bitmap should work.  Is this what you have tried already?

```
self.toolbar.AddLabelTool(some_id, '', wx.ArtProvider.GetBitmap(wx.ART_FILE_SAVE))

```

---

### Post by turvyc on 2010-04-28
Thanks for the reply, Robots,

Your solution does work for the list of default images listed at [the wxPython docs]("http://www.wxpython.org/docs/api/wx.ArtProvider-class.html"), but this list is a bit incomplete . . . for example, it doesn't have a Print Preview bitmap or a proper Help bitmap, while the [standard button IDs]("http://www.wxpython.org/docs/api/wx.Button-class.html") have these. 

Using GetBitmap or GetIcon doesn't work for the button IDs:
```
self.preview = wx.ArtProvider.GetBitmap(id=wx.ID_PREVIEW, client=wx.ART_MENU)
```
The id should be a string, and for some reason wx.ID_PREVIEW isn't one, but wx.ART_PRINT *is* one! This works no problem:```

self.Print = wx.ArtProvider.GetBitmap(id=wx.ART_PRINT, client=client)
```

There must be some way to get the default button IDs into the default toolbar IDs . . . right?

Thanks so much for your help!

---

### Post by robots.jpg on 2010-04-30
My understanding is that the stock icons you're trying to use are provided by GTK, so if you create a wx.Button with id wx.ID_PREVIEW (for example) on a Windows platform without GTK, you'll only get the stock "Print Preview" label with no icon.  This is fine for buttons and menu items, but wouldn't work very well for a toolbar.  

On the other hand, I think the stock art providers used with wx.ArtProvider are built in to wx.  You can add your own, but otherwise you're stuck with what's available in that list.  

Hopefully someone will correct me if I'm wrong on any of that.

---

### Post by turvyc on 2010-04-30
You're right, those are just for GTK. That was a very helpful reply! :P

Thanks for your help!

---

### Post by soltanis on 2010-05-01
WxPython tends to not work on Macs.

Just my experience. All I get is a stupid rocketship and my app closing without explanation. No exceptions, no errors, just silently closes.

---

