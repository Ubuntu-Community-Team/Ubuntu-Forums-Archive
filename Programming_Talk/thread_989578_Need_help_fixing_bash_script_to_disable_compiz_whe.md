---
title: "Need help fixing bash script to disable compiz when gaming"
date: 2008-11-21
forum: Programming Talk
---

### Post by Fabio K on 2008-11-21
Hello world! (and ubuntu forum users)

I'm trying to make a shell script to disable Compiz when I start a game and turn it back on when I close it.
So far the script does what it is supposed to do, but I've noticed that the memory usage of it gets too high after playing lots of games. (It starts with 476Kb memory usage. Then it adds 4Kb each time it disables Compiz).

So far, the code is this:

```
#!/bin/bash
# By Fabio K

# First, everything.
# This goes on if the game was checked and it is running:
function gaming {
	echo "$1 is ON";
# I've chosen fusion-icon because when it opens up, it returns to the WM I previously selected on it.
# What if I selected Metacity as my default WM? I switch between them alot...
# But I mostly use Compiz. That's the purpose of this script.
	if [ -z $(pgrep fusion-icon) ];
	then
		echo "Metacity is ON.";
		killall fusion-icon;
	else
		echo "Metacity is OFF, turning ON...";
		killall fusion-icon;
		(metacity --replace &);
	fi
# Wait till the game closes
	while pgrep $1; do sleep 1; done

# OK, now fire up my default WM, whathever it is...
	echo "$1 is OFF";
	compiz_check=$(pgrep fusion-icon)
	if [ -z $compiz_check ];
	then
		echo "fusion-icon is OFF, turning ON...";
		killall metacity;
		(fusion-icon &);
	else
		echo "fusion-icon is ON.";
	fi
# Maybe give a break to the CPU? I think it is useless. But anyway:
	sleep 5
# This "return" is here because for some reason I couldn't understand why this part of the code loops.
	return;
}

# This checks if the game is running:
function check {
	if [ -z $(pgrep $1) ];
	then
		echo "$1 is OFF";
		sleep 1
	else
		gaming $1;
	fi
}

# The games I want it to check. First come, first serve. (Maybe not since it is a loop...)
function games {
	check hl2.exe;
	check hl.exe;
	check darkplaces;
	check quake4;
	check neverball;
	check neverputt;

	sleep 1
}

# Finally, start the checking:
while echo "Checking again..."; do games; done
# Yeah, echo "Checking again..." makes it loop indefinitely. Couldn't think on something better to put on it.
```

If someone knows how can I fix this memory problem, I'd be happy to hear from you

Fabio K

---

### Post by mssever on 2008-11-22
I don't know what's causing your memory problems, but I wrote the following script before I discovered fusion-icon. It works well as a toggle (call it once to switch to Metacity, again to go to Compix). I designed it to power a panel button, so you'd need to remove the prompting bit.

```
[color=#408080][i]#!/bin/bash
[/i][/color]
[color=#19177C]return_val[/color][color=#666666]=[/color]

[color=#008000]**function **[/color]current_window_manager [color=#666666]{[/color]
  [color=#008000]local [/color][color=#19177C]status[/color][color=#666666]=[/color]
  [color=#008000]local [/color][color=#19177C]current_wm[/color][color=#666666]=[/color]
  p compiz [color=#BA2121]"$USER"[/color] > /dev/null 2>&1
  [color=#19177C]status[/color][color=#666666]=[/color][color=#19177C]$?[/color]
  [color=#008000]**if**[/color] [color=#666666][[/color] [color=#19177C]$status[/color] -eq 0 [color=#666666]][/color]; [color=#008000][b]then
    [/b][/color][color=#19177C]current_wm[/color][color=#666666]=[/color]compiz
  [color=#008000][b]else
    [/b][/color]p metacity [color=#BA2121]"$USER"[/color] > /dev/null 2>&1
    [color=#19177C]status[/color][color=#666666]=[/color][color=#19177C]$?[/color]
    [color=#008000]**if**[/color] [color=#666666][[/color] [color=#19177C]$status[/color] -eq 0 [color=#666666]][/color]; [color=#008000][b]then
      [/b][/color][color=#19177C]current_wm[/color][color=#666666]=[/color]metacity
    [color=#008000][b]fi
  fi
  if[/b][/color] [color=#666666][[/color] -z [color=#19177C]$current_wm[/color] [color=#666666]][/color]; [color=#008000][b]then
    [/b][/color][color=#008000]echo[/color] [color=#BA2121]"Unknown current window manager."[/color] >&2
  [color=#008000][b]fi
  [/b][/color][color=#19177C]return_val[/color][color=#666666]=[/color][color=#BA2121]"$current_wm"[/color]
[color=#666666]}[/color]

[color=#008000]**function **[/color]toggle_window_manager [color=#666666]{[/color]
  [color=#008000]local [/color][color=#19177C]current_wm[/color][color=#666666]=[/color]
  current_window_manager
  [color=#19177C]current_wm[/color][color=#666666]=[/color][color=#BA2121]"$return_val"[/color]
  [color=#008000]**case**[/color] [color=#19177C]$current_wm[/color] in
    compiz[color=#666666])[/color]
      metacity --replace
      killall gtk-window-decorator
      [color=#008000]exec [/color]killall compiz
      ;;
    metacity[color=#666666])[/color]
      [color=#008000]exec [/color]compiz --replace
      ;;
    *[color=#666666])[/color]
      [color=#008000]local [/color][color=#19177C]tmp[/color][color=#666666]=[/color][color=#BA2121]`[/color]zenity --entry --title[color=#666666]=[/color][color=#BA2121]"New Window Manager"[/color] --window-icon[color=#666666]=[/color]question --text[color=#666666]=[/color][color=#BA2121]"Enter the command for the window manager you want to run.
Be sure to pass in the --replace or -replace option."[/color] --entry-text[color=#666666]=[/color][color=#BA2121]"metacity --replace"[/color][color=#BA2121]`[/color]
      [color=#008000]**if**[/color] [color=#666666][[/color] -n [color=#BA2121]"$tmp"[/color] [color=#666666]][/color]; [color=#008000][b]then
        [/b][/color][color=#008000]exec[/color] [color=#19177C]$tmp[/color]
      [color=#008000]**else**[/color]
        [color=#408080][i]#exec zenity --error --text="I don't know how to handle the current window manager, nor do I know to which window manager you want to switch."
[/i][/color]        :
      [color=#008000]**fi**[/color]
      ;;
  [color=#008000]**esac**[/color]
[color=#666666]}[/color]

[color=#008000]**function **[/color]main [color=#666666]{[/color]
  zenity --question --text[color=#666666]=[/color][color=#BA2121]"Do you want to switch window managers?"[/color] [color=#666666]&&[/color] toggle_window_manager
[color=#666666]}[/color]

main [color=#BA2121]"$@"[/color]
```

---

### Post by Fabio K on 2008-11-22
Ok, your script works perfectly, but it is a toggle button.
I'm trying to make something similar to what happens in Vista:
1. The effects are on while you are doing normal stuff
2. When you launch a fullscreen OpenGL or DirectX app, the WM changes to the basic theme (no effects), and keeps this way until you take the focus from the game or quits.

Ever since I don't know how to detect whether the focus is or not on the game, and I want the effects to be turned off even if it is a window, I made this script that is loaded when I start gnome-session and keeps looping the 'check' so it can know if the game on that list is running or not.

But with that memory problem, if I start and stop constantly games, it'll easily grow to something huge on the RAM (ok, not that big...), and eventually it will be killed automatically (I have no idea why it happens).

I'm going to try to adapt your script to mine and see if it works better than mine, if it uses less CPU time and RAM. Mine runs using 1% CPU (nice -n 19) and 476Kb +4Kb each time compiz is disabled.

Fabio K

---

### Post by raf_kig on 2008-11-22
Just do it like that:
Save that somewhere in $PATH as eg gamelaunch and start your games with
'gamelaunch gamename'
it will replace compiz with metacity, run the game, and restart compiz as soon as the game exits.

```

#!/bin/bash
game=$*
metacity --replace
killall gtk-window-decorator
killall compiz
exec $game
compiz --replace

```

Regards

raf

---

### Post by Fabio K on 2008-11-22
> **raf_kig said:**
> Just do it like that:
Save that somewhere in $PATH as eg gamelaunch and start your games with
'gamelaunch gamename'
it will replace compiz with metacity, run the game, and restart compiz as soon as the game exits.

```

#!/bin/bash
game=$*
metacity --replace
killall gtk-window-decorator
killall compiz
exec $game
compiz --replace

```

Regards

raf

Firstly I thought about that, but how about the Steam games (Half-life and Mods)? I keep Steam running on the background, and since the games are launched from Steam, it's the same as not having Compiz running while it is on.

EDIT: I think I've got a way around my problem using your idea. What if I made my script start ONLY if Steam was running?

EDIT: Never mind.. It would be the same. But if I launched the games through launchers, and not directly through Steam, it would be much more clever, wouldn't it? (Alias the script in the .bashrc would work?)

---

### Post by Fabio K on 2008-11-22
Ok, how about this:
I schedule a cron job set to kill the script and launch again every 5 minutes.
Then it would be always on and never exceeding the amount of RAM spent for 5 minutes!
It could work...

Fabio K

---

### Post by Fabio K on 2008-11-22
Never mind the cron job, the launcher script or the weird idea I had of using alias on .bashrc...

Remove all the "echo" commands and it stays 476Kb on RAM (So far I tested it for 15 minutes opening and closing games)
I'll test for a day and see the results.

Oh, zenity seems a nice program. Never heard of it. I'll google it to see how to use it.

Thanks all of you who helped me.

Fabio K

---

