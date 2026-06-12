---
title: "Anjuta debugging (cin)"
date: 2008-01-19
forum: Programming Talk
---

### Post by breaking on 2008-01-19
I'm in Anjuta 2.2.0. I'm debugging a program I just wrote with the debugger plugin. The problem is that the debugger freezes when it hits a cin statement. 

I assume it's waiting for input (I know that the terminal based gdb asks you for input).. the main Anjuta GUI is still responsive, but nothing pops up and asks me to enter anything.. it just sits there with the spinning clock cursor! cout doesn't freeze the debugger (and I do see cout output in the "Messages" pane). I can step into and through cout, but the instant I click "step into function" on cin, the debugger freezes.

I have the "Terminal" tab open but all I get is the brian@brians:~$ prompt.. nothing from the debugger. 

Maybe the way to get it to use the Terminal tab for console I/O is to select "Run In Terminal" from the debug menu, but when I select that and start the debugger the whole interface freezes up and I have to sigkill.

Can anyone help? :KS

---

### Post by breaking on 2008-01-20
Anyone?

---

### Post by breaking on 2008-01-23
Anyone anyone :-\"

---

### Post by kh_naba on 2008-02-05
You should report a bug at [http://bugzilla.gnome.org](http://bugzilla.gnome.org)

---

