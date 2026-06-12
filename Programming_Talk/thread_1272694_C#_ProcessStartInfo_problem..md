---
title: "C# ProcessStartInfo problem."
date: 2009-09-22
forum: Programming Talk
---

### Post by dchurch24 on 2009-09-22
Hi all,

I have the following C# code (mono):

```

        public void start_proc(String SongPath)

        {
			
			SongPath = SongPath.Replace("*","");//.Replace ("/","\/");
			SongPath = SongPath.Substring (4,SongPath.Length-4);
	
            System.Diagnostics.ProcessStartInfo psi = new System.Diagnostics.ProcessStartInfo("vlc", SongPath);

            psi.RedirectStandardOutput = true;

            psi.WindowStyle = System.Diagnostics.ProcessWindowStyle.Hidden;

            psi.UseShellExecute = false;

            System.Diagnostics.Process proc;

            proc = System.Diagnostics.Process.Start(psi);

            System.IO.StreamReader myOutput = proc.StandardOutput;



            proc.WaitForExit();



            replytoclient();            

        }

```

It runs fine, apart from when I send the command:

```

*vlc -I ncurses \'/home/dave/Music/Catatonia/Catatonia - Karaoke Queen.mp3\' vlc:quit*

```

I know. I don't like Catatonia much either, but I didn't realise that C# wouldn't.

If I take out everything after 'ncurses' it shells VLC perfectly.

If I leave it in there, I get.

```

VLC media player 0.8.6e Janus
Error opening terminal: unknown.

```

I've tried escaping the ' and the / but nothing seems to work.

I can copy the line and execute it from the terminal, and sure enough VLC starts using ncurses and plays the specified song.

---

### Post by directhex on 2009-09-22
Try *NOT* escaping anything. escaping is for shell expansion, and you're not in a shell

---

### Post by doas777 on 2009-09-22
in C# on windows, it is usually recomended to proceed path strings with @ to tell it to escape the symbolic characters, but as DirectHex pointed out, you are just crafting a command, so give it to the interpreter exactly as though you had typed it by hand.

I really hate spaces in file names. who thought that would be a good Idea?

---

### Post by dchurch24 on 2009-09-23
I know what you mean about spaces!

However, in this instance, it seems that VLC doesn't like being shelled with the 'ncurses'. I took that out, and it plays the song fine.

So...I figured, I'd just run it 'hidden' or at least 'minimised', but it ignores the psi.WindowStyle = System.Diagnostics.ProcessWindowStyle.Hidden;
line for some reason.

So...for the time being I thought I'd just make my app full-screen and always-on-top. I've got the always-on=-top bit working, but I can't seem to make the gtk window fullscreen by default.

Any ideas?

PS. I must confess, this is becoming a very confusing project to work on. I have a windows front-end written in VB.net that sends a command to the c# (mono - Linux) listener, (then turns into a listener itself), that plays a song, waits for it to finish, then sends a command back to the VB program to tell it to send the path to another song to start playing, all the while telling a USB 8-way relay which speakers to turn on so I can use my touch screen to press a 'room' (well, flat style button actually) and have the music play in that room.  Flipping between similar languages like that is starting to hurt my brain!

---

### Post by dchurch24 on 2009-09-23
> **directhex said:**
> Try *NOT* escaping anything. escaping is for shell expansion, and you're not in a shell

Yes. Good call. I did realise that, and the only reason the escape chars are there is because I was clutching as straws at this point. I've tried it like it is above, with escape chars before each /, without any at all, etc... but none of those work.

If I take out the ncurses param. and pass the path of the song in a String rather than through the IP listener, then it works.

It's odd, as the String is the same regardless of how I send it.!??

---

### Post by directhex on 2009-09-23
Thinking about it...

the ncurses UI is going to want a controlling terminal, as NCurses requires a PTY to draw into. When you're passing that flag to make it use ncurses, it tries and fails to get a controlling terminal (since it's not running in one)

Does "dummy" instead work?

---

### Post by dchurch24 on 2009-09-24
Ooh, not sure. I'll give that a try when I get home. Thanks.

However, I have changed it to re-write it to a String object, then I start the process with that argument, and viola! It plays!

The only thing is that it's still showing a 'normal' window. I will try Dummy later.

---

