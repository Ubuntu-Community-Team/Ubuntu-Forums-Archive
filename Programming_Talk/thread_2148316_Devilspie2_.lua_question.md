---
title: "Devilspie2 .lua question"
date: 2013-05-24
forum: Programming Talk
---

### Post by Jacob-Gates on 2013-05-24
I'm trying to get Devilspie2 working and it is set up with .lua files. I have never typed up a .lua file before so I have been following this not so great tutorial here:
[http://www.gusnan.se/devilspie2/manual.php#get_window_name](http://www.gusnan.se/devilspie2/manual.php#get_window_name)

I have searched and searched and there isn't much online to help me with this so here I am. I am trying to get Terminal on my background like it is apart of my wallpaper. I don't know if there is a better way than using Devilspie2 so if someone does know an easier way I'll be happy to give it a try. Anyways, here is my script that I wrote from what little I understand from the link above:
```
if 	(get_application_name()=="gnome-terminal") 	then
	get_window_is_maximized_vertically();
	set_window_position(300,300);
	undecorate_window();
	pin_window();
	stick_window();
	set_window_below();
	get_window_type("WINDOW_TYPE_UTILITY");
	end
```

When I run Devilspie2 by typing "devilspie2" in terminal it doesn't output anything but I don't get my "user@computer~$" either so it's like it just froze or something. And there is no terminal to be found. I'm not really sure if the scripting I wrote tells it to actually open terminal but it didn't say anything about that in the tutorial. If anyone knows what I have done wrong please let me know, Thanks.

---

### Post by ohnonot on 2013-05-25
i've tried devilspie once, unfortunately i don't remember if it was devilspie or devilspie2, but i remember that i stopped using it because i didn't have to because basically my window manager was able to achieve the same things. openbox.
what window manager are you using? and what terminal emulator?
if you want the terminal to be directly on your wallpaper, you don't have desktop icons?

edit: also i never created any lua scripts for it.
lua is used a lot with conky, so for practical tips for lua you might start there. (loads of conky threads, here on uf, but also e.g. on crunchbang forums)

---

### Post by Jacob-Gates on 2013-05-25
> **ohnonot said:**
> i've tried devilspie once, unfortunately i don't remember if it was devilspie or devilspie2, but i remember that i stopped using it because i didn't have to because basically my window manager was able to achieve the same things. openbox.
what window manager are you using? and what terminal emulator?
if you want the terminal to be directly on your wallpaper, you don't have desktop icons?

edit: also i never created any lua scripts for it.
lua is used a lot with conky, so for practical tips for lua you might start there. (loads of conky threads, here on uf, but also e.g. on crunchbang forums)

I tried devilspie but apparently it doesn't work with Gnome 3 and I read that Devilspie2 is supposed to work with Gnome 3. I'm using the stock window's manager, what ever that is (or maybe what ever gnome changed it to) and gnome-terminal. I don't have desktop icons, I'm doing this because I'm trying to make my computer look all futuristic and stuff and I think it would be awesome to have terminal on the wallpaper.

---

### Post by ohnonot on 2013-05-26
it is possible!
but regardless of window managers or devilspie, some terminal emulator applications have this option in their preferences, either as check boxes or as command line options: disable menu, disable window borders, disable scrollbar, start full screen. sth like that.

but i think the best way to go is with command line options (because that way you can still open a second terminal normally)
so, try to create an entry in autostart (gnome has a gui for that) that starts your favorite terminal emulator in fullscreen, completely borderless mode when you log in!

to find out about command line options, do this:
open a terminal window, type "man gnome-terminal-emulator".
the command for the terminal emulator might be different, but the "man" is the magic word.
it stands for manual and you can use it on any installed application.

edit: i'm not so sure if this is possible with the default gnome terminal, but it is definitely possible with others, so you might want to consider installing another terminal emulator alongside gnome. 
also some allow for different profiles, so you could set up a profile for the "background terminal" and start that with autostart, thus you could somewhat avoid using the command line and man.
but many apps have more command line options than the ui reveals!

---

### Post by Jacob-Gates on 2013-05-26
yeah I have used man before, it can be really helpful. So with this way I can still open a second terminal in a window like normal right? The only terminal without a border will be the first one and all others will be normal, right?

---

### Post by ohnonot on 2013-05-26
> **Jacob-Gates said:**
> yeah I have used man before, it can be really helpful. So with this way I can still open a second terminal in a window like normal right? The only terminal without a border will be the first one and all others will be normal, right?
i can't answer your question because you haven't told us what you are actually doing now.
you say "this way" but i don't know which way you're going yet.
my advice was very general.
i will be happy to help you achieve what you want, but next is you telling us what you are trying and what is working and what not and which terminal you are using and all that.

edit: i just installed vanilla ubuntu 13.04 to be able to help better, and tried to achieve what you want.
it's possible, as i described, there's options in gnome terminal like disable menubar and scrollbar. then i started gnome-terminal with```
gnome-terminal --geometry 1280x800
```- which happens to be my screen resolution.
and lo, the terminal fills my whole screen, with a nice, semi-transparent bg. somehow it is even clever enough to leave space for the top bar and the side launcher. 
so all you'd have to do is to make that stick so it autostarts when you log in.
unfortunately there seems to be no menu anymore, but i guess if you just type autostart into the dash, it should pop up.

but at least on my machine all this is taking resources like crazy and i just happen to know that you can achieve the same without stressing your cpu at all.

---

### Post by Jacob-Gates on 2013-05-26
> **ohnonot said:**
> i can't answer your question because you haven't told us what you are actually doing now.
you say "this way" but i don't know which way you're going yet.
my advice was very general.
i will be happy to help you achieve what you want, but next is you telling us what you are trying and what is working and what not and which terminal you are using and all that.

edit: i just installed vanilla ubuntu 13.04 to be able to help better, and tried to achieve what you want.
it's possible, as i described, there's options in gnome terminal like disable menubar and scrollbar. then i started gnome-terminal with```
gnome-terminal --geometry 1280x800
```- which happens to be my screen resolution.
and lo, the terminal fills my whole screen, with a nice, semi-transparent bg. somehow it is even clever enough to leave space for the top bar and the side launcher. 
so all you'd have to do is to make that stick so it autostarts when you log in.
unfortunately there seems to be no menu anymore, but i guess if you just type autostart into the dash, it should pop up.

but at least on my machine all this is taking resources like crazy and i just happen to know that you can achieve the same without stressing your cpu at all.

When I said "this way" I was talking about exactly what you told me to do i that post with the terminal commands. That way when I open a second terminal it is opened in the default profile that doesn't hide anything. I got it to work pretty well actually and what I did was set up a second profile in terminal that was the default and created a scripts in autostart that opens that terminal profile. The only problem is the window border is still there. I can't find either an option or a command that hides the border. do you know of a way to do that?

---

### Post by ohnonot on 2013-05-27
strange, the fullscreen thing i described does not seem to work properly.
i found some interesting answers here:
[http://askubuntu.com/questions/142487/how-to-start-terminal-in-full-screen](http://askubuntu.com/questions/142487/how-to-start-terminal-in-full-screen)

(i did a websearch for you! it was 'ubuntu terminal full screen')

PS: the design of the unity desktop makes it really difficult to Do Things Yourself.
i'll be happy to assist further.

---

### Post by Jacob-Gates on 2013-05-27
> **ohnonot said:**
> strange, the fullscreen thing i described does not seem to work properly.
i found some interesting answers here:
[http://askubuntu.com/questions/142487/how-to-start-terminal-in-full-screen](http://askubuntu.com/questions/142487/how-to-start-terminal-in-full-screen)

(i did a websearch for you! it was 'ubuntu terminal full screen')

Oh no, i'm not not trying to get it to go fullscreen. I just want it to be in a part of the screen but I don't want the window border to be there. I'm sorry i didn't make that clear.

---

### Post by gusnan on 2013-06-18
> When I run Devilspie2 by typing "devilspie2" in terminal it doesn't output anything but I don't get my "user@computer~$" either so it's like it just froze or something.

You are supposed to have devilspie2 running in the background - When you do that, the devilspie2 scripts will be run on every window that is opened. So, keep the script you have in the first post in this thread, run devilspie2 (either in a terminal or some other way), make sure it is running, and then start another terminal. 

However, I don't know if that 
```
if     (get_application_name()=="gnome-terminal")     then
```
catches gnome-terminal correctly - You need to get the application name exactly right (uppercase and lowercase characters). - you can use the debug functions in devilspie2 to make sure that you got the application (or window) names correct.

Devilspie2 is meant to be running all the time (Probably easiest done by putting it into the autostart of your desktop when all your scripts are done and correct).

---

### Post by ohnonot on 2013-07-05
if anybody is still interested:

-- try using terminator instead of gnome-terminal. it is able to achieve most of what is needed to get a cool terminal background.
```
sudo apt-get install terminator
```
here's my ~/.config/terminator/config:
```
[global_config]
  tab_position = hidden
  title_hide_sizetext = True
  borderless = True
  focus = system
  sticky = True
[keybindings]
[profiles]
  [[default]]
    use_system_font = False
    background_darkness = 0.0
    background_type = transparent
    scrollbar_position = hidden
    foreground_color = "#000000"
    icon_bell = False
    show_titlebar = False
    antialias = False
    font = Fixed 10
    background_color = "#ffffff"
    allow_bold = False
    scrollback_infinite = True
[layouts]
  [[default]]
    [[[child1]]]
      type = Terminal
      parent = window0
      profile = default
    [[[window0]]]
      type = Window
      parent = ""
[plugins]
```- but all this can be achieved through the preferences dialog.
(you might want to [enable pixel fonts]("http://iamfuss.deviantart.com/journal/How-to-install-artwiz-pixel-fonts-in-Ubuntu-226000883"))

-- with these default settings i just add "terminator" to startup applications.

-- the only remaining problem is to have the terminal "always on bottom", so that the transparent terminal will never appear on top of your apps. which is not possible to achieve with terminator or the version of devilspie2 that is in the repos (i did not actually try this, just saw that in the tutorial from post 1, it says set_window_below is not available before version 0.21 and i have 0.15 installed on ubuntu LTS 12.04. maybe gusnan could comment on this?)

-- i ended up using gdevilspie (which is based on devilspie, NOT devilspie2). it works. the rule i set up looks like this: ```
; generated_rule terminator
( if 
( begin 
( is ( window_class ) "Terminator" )
) 
( begin 
( pin )
( undecorate )
( skip_pager )
( skip_tasklist )
( below )
( println "match" )
)
)
```you can save it to ~/.devilspie/terminator.ds.
(i have created it with the gui)

---

