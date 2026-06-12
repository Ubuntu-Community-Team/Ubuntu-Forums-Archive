---
title: "Where did bittorrent go??"
date: 2008-10-23
forum: New to Ubuntu
---

### Post by faraz_k86 on 2008-10-23
I downloaded bittorrent application, along with the GUI.

But i cant find it anywhere in the menu.

plz help me out, how do i find it?

---

### Post by alphaniner on 2008-10-23
Try right clicking on Applications (the word itself) and go to Edit Menus.

---

### Post by faraz_k86 on 2008-10-23
thx for the rply but its not in there either

---

### Post by appi2012 on 2008-10-23
Did you download it from a website? You actually don't need to.

Ubuntu comes with a bittorrent client. Go to Applications -> Internet -> Transmission Bittorent Client. You can use that to use bittorent.

Hope that helps.

---

### Post by Keen101 on 2008-10-23
The default place for firefox to download is either your Desktop or your Home folder. **check your home folder.**

 But, just so you know in >Applications >Internet >Transmission you have a bittorrent client already installed by default.

---

### Post by faraz_k86 on 2008-10-23
i downloaded it from synaptics package manager

---

### Post by snova on 2008-10-23
Not all BitTorrent clients have GUI's, so it might not be in the menu. It depends on the client. Which one was it?

Edit: Oops, missed where you said you installed the GUI... but adding it to the menu manually isn't difficult.

---

### Post by vjones777 on 2008-10-23
I'm not sure how to find which menu it got placed in.  A work around would be to create one (and later delete the original if/when you ever find it).

To find the program itself, Alt-F2 and type in bittorrent - it should be listed.  Then click on the entry in the list and the path to the program should be revealed.  Use that to create your menu item.

Hope that helps.

---

### Post by faraz_k86 on 2008-10-24
i did that, but it only brings up transmission bittorrent??

---

### Post by 3rdalbum on 2008-10-24
There's a link in my signature that should help you; it's about "Where did my program go" and how to add it to the menu.

---

### Post by faraz_k86 on 2008-10-24
the gui is not there. still cant find it

---

### Post by t0p on 2008-10-24
Right-click on **Applications**, select **Edit Menus**.  Now, on the right hand side, click on **Add New Item**.  Type *bittorrent* in the appropriate places.  Now it should appear in the menu.

Anyway, what happens if you press **Alt+F2** and type in *bittorrent*?  Or if you open a terminal (**Applications > Accessories >Terminal**) and type *bittorrent* in there?

---

### Post by forger on 2008-10-24
What is the name/title of the **package**/application you downloaded from synaptics?

---

### Post by forger on 2008-10-24
If it was **bittorrent-gui** go to Applications > Accessories > Terminal and execute:
```

btcompletedirgui.bittorrent
btdownloadgui.bittorrent

```

If nothing comes up, copy paste this command and reply with the full output:
```
dpkg -l | grep "bitt\|torrent"
```

But why would you need such an old client? Deluge or transmission are much better and richer in features.

---

