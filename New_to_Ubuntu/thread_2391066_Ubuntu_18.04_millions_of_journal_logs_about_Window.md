---
title: "Ubuntu 18.04 millions of journal logs about Window manager warnings"
date: 2018-05-05
forum: New to Ubuntu
---

### Post by izopi4a on 2018-05-05
Hi, i am running ubuntu 18.04, first i tough i have some gnome extension messing with me, but than i disabled them all and i am getting this journal warnings that after ~10 mins makes every window created super laggy.
Once system has been running for ~30 mins, when i try to open a Firefox dropdown ( menu ) it literaly takes 2 secs, same in every other window i have opened. If i click "windows" button to show activities again it takes like 2-3 secs.

```

journalctl --since="1 minutes ago" _COMM=gnome-shell
-- Logs begin at Tue 2018-05-01 10:08:31 EEST, end at Sat 2018-05-05 20:47:16 EEST. --
&#1084;&#1072;&#1081; 06 00:49:18 izopi4a-desktop org.gnome.Shell.desktop[1720]: Window manager warning: Window 0x5009020 (win549) sets an MWM hint indicating it isn't resizable, but sets min size 1 x 1 and max size 2147483647 x 2147483647; this doesn't make much sense.
&#1084;&#1072;&#1081; 06 00:49:18 izopi4a-desktop org.gnome.Shell.desktop[1720]: Window manager warning: Window 0x500902d (win551) sets an MWM hint indicating it isn't resizable, but sets min size 1 x 1 and max size 2147483647 x 2147483647; this doesn't make much sense.
&#1084;&#1072;&#1081; 06 00:49:18 izopi4a-desktop org.gnome.Shell.desktop[1720]: Window manager warning: Window 0x5009032 (win552) sets an MWM hint indicating it isn't resizable, but sets min size 1 x 1 and max size 2147483647 x 2147483647; this doesn't make much sense.
&#1084;&#1072;&#1081; 06 00:49:19 izopi4a-desktop org.gnome.Shell.desktop[1720]: Window manager warning: Window 0x500903a (win553) sets an MWM hint indicating it isn't resizable, but sets min size 1 x 1 and max size 2147483647 x 2147483647; this doesn't make much sense.
&#1084;&#1072;&#1081; 06 00:49:19 izopi4a-desktop org.gnome.Shell.desktop[1720]: Window manager warning: Window 0x500903f (win554) sets an MWM hint indicating it isn't resizable, but sets min size 1 x 1 and max size 2147483647 x 2147483647; this doesn't make much sense.
&#1084;&#1072;&#1081; 06 00:49:19 izopi4a-desktop org.gnome.Shell.desktop[1720]: Window manager warning: Window 0x5009049 (win556) sets an MWM hint indicating it isn't resizable, but sets min size 1 x 1 and max size 2147483647 x 2147483647; this doesn't make much sense.
&#1084;&#1072;&#1081; 06 00:49:19 izopi4a-desktop org.gnome.Shell.desktop[1720]: Window manager warning: Window 0x5009053 (win558) sets an MWM hint indicating it isn't resizable, but sets min size 1 x 1 and max size 2147483647 x 2147483647; this doesn't make much sense.
&#1084;&#1072;&#1081; 06 00:49:19 izopi4a-desktop org.gnome.Shell.desktop[1720]: Window manager warning: Window 0x5009058 (win559) sets an MWM hint indicating it isn't resizable, but sets min size 1 x 1 and max size 2147483647 x 2147483647; this doesn't make much sense.
&#1084;&#1072;&#1081; 06 00:49:19 izopi4a-desktop org.gnome.Shell.desktop[1720]: Window manager warning: Window 0x5009067 (win562) sets an MWM hint indicating it isn't resizable, but sets min size 1 x 1 and max size 2147483647 x 2147483647; this doesn't make much sense.
&#1084;&#1072;&#1081; 06 00:49:19 izopi4a-desktop org.gnome.Shell.desktop[1720]: Window manager warning: Window 0x500906c (win563) sets an MWM hint indicating it isn't resizable, but sets min size 1 x 1 and max size 2147483647 x 2147483647; this doesn't make much sense.
&#1084;&#1072;&#1081; 06 00:49:20 izopi4a-desktop org.gnome.Shell.desktop[1720]: Window manager warning: Window 0x5009074 (win564) sets an MWM hint indicating it isn't resizable, but sets min size 1 x 1 and max size 2147483647 x 2147483647; this doesn't make much sense.
&#1084;&#1072;&#1081; 06 00:49:20 izopi4a-desktop org.gnome.Shell.desktop[1720]: Window manager warning: Window 0x5009079 (win565) sets an MWM hint indicating it isn't resizable, but sets min size 1 x 1 and max size 2147483647 x 2147483647; this doesn't make much sense.
&#1084;&#1072;&#1081; 06 00:49:20 izopi4a-desktop org.gnome.Shell.desktop[1720]: Window manager warning: Window 0x5009081 (win566) sets an MWM hint indicating it isn't resizable, but sets min size 1 x 1 and max size 2147483647 x 2147483647; this doesn't make much sense.
&#1084;&#1072;&#1081; 06 00:49:20 izopi4a-desktop org.gnome.Shell.desktop[1720]: Window manager warning: Window 0x5009086 (win567) sets an MWM hint indicating it isn't resizable, but sets min size 1 x 1 and max size 2147483647 x 2147483647; this doesn't make much sense.
&#1084;&#1072;&#1081; 06 00:49:20 izopi4a-desktop org.gnome.Shell.desktop[1720]: Window manager warning: Window 0x500908b (win568) sets an MWM hint indicating it isn't resizable, but sets min size 1 x 1 and max size 2147483647 x 2147483647; this doesn't make much sense.
&#1084;&#1072;&#1081; 06 00:49:21 izopi4a-desktop org.gnome.Shell.desktop[1720]: Window manager warning: Window 0x5009090 (win569) sets an MWM hint indicating it isn't resizable, but sets min size 1 x 1 and max size 2147483647 x 2147483647; this doesn't make much sense.

```

---

