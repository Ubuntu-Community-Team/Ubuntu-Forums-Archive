---
title: "I want to do something with vim and the terminal. Is this possible?"
date: 2012-10-22
forum: Programming Talk
---

### Post by Smedvig on 2012-10-22
I recently started using vim, and here's what I'd like to be able to do:

1. SSH into a server.
2. Browse around the directories, and open some files with vim in different tabs ([FONT=Courier New]vim -p file1.pl file2.pl...[/FONT]) and edit those files.
3. While those files are still open in vim, switch back to the command line (maybe using [FONT=Courier New]screen[/FONT], or ctrl-z), and navigate to a different directory.
4. Open a file in that directory in the same instance of vim from before, in a new tab.

Step 4 is what I'm having trouble with. I realize I could switch back to vim and do [FONT=Courier New]:tabnew /absolute/path/to/file[/FONT] , but that's annoying because I've already navigated there using the command line. This may seem like a trivial point, but I have to do this a lot from different directories and the paths are long, so it seems like there should be a more efficient way... maybe a command from the command line that somehow calls upon that particular vim instance.

If this is possible with emacs but not vim, I'll take that too.

Thanks for any help!

---

### Post by spjackson on 2012-10-23
I don't know that it's possible to communicate with a running instance of vim to get it to open another file (and tab); I haven't heard of it, but it may be possible.

I'm not familiar with using tabs in emacs (or in vim for that matter), although I do know that [there is such a thing]("http://emacswiki.org/emacs/TabBarMode").

If I "ssh -X" to another server, I can then do:
```

# start a daemon
emacs -daemon
# start a GUI connected to the daemon opening 1 file
emacsclient -c a.c &
# open another file in the existing GUI
emacsclient b.c &

```
Of course, you can also run a shell window inside emacs, which means you don't need server/client stuff, for example eshell has the builtin command find-file <filename> which opens a new edit buffer for the given file.

However, I don't know emacs that well any more I'm afraid. I keep meaning to relearn, but I still know vim better.

---

### Post by trent.josephsen on 2012-10-23
I looked in the manpage because I was pretty sure there is a way to do this, and I was right, although it's kind of deeply buried.

```
       --remote    Connect to a Vim server and make it edit the files given in
                   the rest of the arguments.  If no server is found a warning
                   is given and the files are edited in the current Vim.

<snip>

       --serverlist
                   List the names of all Vim servers that can be found.

       --servername {name}
                   Use  {name}  as the server name.  Used for the current Vim,
                   unless used with a --remote argument, then it's the name of
                   the server to connect to.
```

So to answer your question, you could start Vim as follows:

```
% vim --servername foo
```

and run this to edit files in it:

```
% vim --remote --servername foo file_1 file_2
```

Seems the default servername is VIM both when starting up and when connecting, so if you only have one instance open you wouldn't need to worry about that argument; it would just be `vim` and `vim --remote file_1 ...`.

---

