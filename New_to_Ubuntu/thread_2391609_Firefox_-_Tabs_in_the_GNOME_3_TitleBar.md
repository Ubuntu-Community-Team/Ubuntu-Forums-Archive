---
title: "Firefox - Tabs in the GNOME 3 TitleBar"
date: 2018-05-11
forum: New to Ubuntu
---

### Post by garzet on 2018-05-11
Hey. I'm new to Linux, but I'm starting to make my way around and looks like I might stick to it.

One thing that bothers me and I find silly is how you loose plenty of Firefox space because title bar.
IMAGE: [https://ibb.co/jggj5d](https://ibb.co/jggj5d)

Can I have tabs move up in the title bar or somehow remove titlebar when the window is maximized but move the minimze, maximize and close buttons inline with the tabs?
Two reasons why this bothers me:
[LIST=1]
[*]You loose pixels 
[*]More importantly, you have to aim for the tab now with the mouse since tab is not at the edge of the screen. 
[/LIST]

Can this be done in infinitely customizable linux world?

---

### Post by DuckHook on 2018-05-11
[LIST=1]
[*]FF is not Linux. It is a product of the Mozilla Foundation. However, it is FOSS.
[*]Both Linux and FOSS are only "infinitely customizable" if you are prepared to rewrite source code and compile your very own, very special, very private version/app. Otherwise, it is not realistic to expect infinite customizability in anything.
[*]The keyboard shortcut for easily rotating between tabs is: <Ctrl> + <Tab>
[*]Min/Max/Close (among other options) can always be invoked, in any window, with <Alt> + <Space>
[*]If you want to free up as much screen real estate as possible, instead of maximizing, go into full screen mode with <F11>.
[/LIST]
Combining 3, 4 & 5 above gives you all kinds control without ever having to touch the mouse.

---

### Post by monkeybrain20122 on 2018-05-13
For gnome-shell try the hide top bar [extension]("https://extensions.gnome.org/extension/545/hide-top-bar/").

But it looks a lot better in the unity-session.

---

### Post by tea for one on 2018-05-14
In Firefox 60, there is a setting which will remove the title bar:-

Open the menu (hamburger style icon) > Customize > Bottom left is a check box for Title Bar

---

### Post by kerry_s on 2018-05-14
for buttons on the left.
userChrome.css

```

@namespace url("http://www.mozilla.org/keymaster/gatekeeper/there.is.only.xul");

#titlebar-max {
  -moz-box-ordinal-group: 0;
}

#titlebar-content {
  direction: rtl;
}

#TabsToolbar {
  direction: rtl;
}

#tabbrowser-tabs {
  direction: ltr;
}




```

---

### Post by monkeybrain20122 on 2018-05-14
> **kerry_s said:**
> for buttons on the left.
userChrome.css

```

@namespace url("http://www.mozilla.org/keymaster/gatekeeper/there.is.only.xul");

#titlebar-max {
  -moz-box-ordinal-group: 0;
}

#titlebar-content {
  direction: rtl;
}

#TabsToolbar {
  direction: rtl;
}

#tabbrowser-tabs {
  direction: ltr;
}




```
But this works only for Firefox, it would be weird if everything else has buttons on the right but FF has them on the left.

---

### Post by kerry_s on 2018-05-14
it's for people who have there close/min/max on the left & don't want firefox to have it on the right.

---

### Post by garzet on 2018-05-18
> **tea for one said:**
> In Firefox 60, there is a setting which will remove the title bar:-

Open the menu (hamburger style icon) > Customize > Bottom left is a check box for Title Bar

Thank you! This is almost perfect (you still cannot click on the edge of the screen, but its good enugh)

---

### Post by tea for one on 2018-05-19
> **garzet said:**
> Thank you! This is almost perfect (you still cannot click on the edge of the screen, but its good enugh)

Splendid - I'm pleased that your difficulty has been addressed.

If you could use the thread tools and mark the problem as solved then it could possibly help other Ubuntu/Firefox users

---

