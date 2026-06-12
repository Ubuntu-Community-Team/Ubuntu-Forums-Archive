---
title: "bzr launchpad-login doesn't work"
date: 2010-06-24
forum: Programming Talk
---

### Post by fiddler616 on 2010-06-24
Hello,

So I've been working on a project hosted on Launchpad, which uses Bazaar. I finally finished a version good enough to upload back to Launchpad, but Bazaar is not working for me. Like so:

```

$ bzr launchpad-login tsmacdonald
$      0KB/s |

```

That is, it briefly flashes the loading bar, and then has my bash prompt outputted on top of it, and nothing else happens. [Here's a screenshot]("http://i.imgur.com/KdBnl.png") (as you can see, I tried it in both terminator and xterm to make sure it wasn't a terminal bug). I've tried Googling, but apparently I'm the only one this happens to.

Any suggestions?


Thanks in advance.

---

### Post by jonthysell on 2010-06-25
Have you made sure that you've assoiated your ssh public key with your launchpad account? Also, (can't tell by your post if you've tried multiple times) but launchpad-login should only need to be done once, and I'm pretty sure there's no output.

---

### Post by nvteighen on 2010-06-25
Yes, very certainly your issue is related to your SSH-leys configuration in your Launchpad account. Look at [https://help.launchpad.net/YourAccount/CreatingAnSSHKeyPair](https://help.launchpad.net/YourAccount/CreatingAnSSHKeyPair)

---

### Post by fiddler616 on 2010-06-25
> **nvteighen said:**
> Yes, very certainly your issue is related to your SSH-leys configuration in your Launchpad account. Look at [https://help.launchpad.net/YourAccount/CreatingAnSSHKeyPair](https://help.launchpad.net/YourAccount/CreatingAnSSHKeyPair)

Well, now I can log in, but despite pushing my changes, they're not reflected in the branch on Launchpad. Then I ran "bzr commit", and a log file opened up in vim that said:
> 
-------This line and the following will be ignored-----------
modified:
    pttengine.py
    pttgames/tictactoe/tictactoe.py
    pyctactoe
unknown:
    pttgames/go/

And it's true--over [here ]("http://bazaar.launchpad.net/~tsmacdonald/pyctactoe/pyctacgo/files/head:/pttgames/")there should be a folder called "go" with all kinds of goodness inside.

For the record, I've been using [these]("https://help.launchpad.net/Code/UploadingABranch") instructions.

---

### Post by nvteighen on 2010-06-26
> **fiddler616 said:**
> Well, now I can log in, but despite pushing my changes, they're not reflected in the branch on Launchpad. Then I ran "bzr commit", and a log file opened up in vim that said:


And it's true--over [here ]("http://bazaar.launchpad.net/~tsmacdonald/pyctactoe/pyctacgo/files/head:/pttgames/")there should be a folder called "go" with all kinds of goodness inside.

For the record, I've been using [these]("https://help.launchpad.net/Code/UploadingABranch") instructions.

Ugh... let's see.

The standard procedure to follow is:
1. Code!
2. bzr add (to add everything)
3. bzr commit -m "Message"
4. bzr push

That's all. Now, I highly recommend you commit and then merge with trunk again, adapt your code, commit and push; you're working on a slightly outdated codebase: currently PycTacToe's trunk detects games automatically so there's no need to modify anything outside your game. In its current fashion, a merging of your branch with trunk would be impossible.

---

### Post by fiddler616 on 2010-06-28
> **nvteighen said:**
> Ugh... let's see.

The standard procedure to follow is:
1. Code!
2. bzr add (to add everything)
3. bzr commit -m "Message"
4. bzr push

That's all. Now, I highly recommend you commit and then merge with trunk again, adapt your code, commit and push; you're working on a slightly outdated codebase: currently PycTacToe's trunk detects games automatically so there's no need to modify anything outside your game. In its current fashion, a merging of your branch with trunk would be impossible.

I'm in the process of moving computers, and since PycTacToe was on the old one, I took  this as an opportunity to start anew on a new machine. So I registered my SSH key, branched pyctactoe, added my go folder (and did not change anything in PTT's "core"), and...well, here's my terminal:

```
timmy@macpherson:~$ bzr launchpad-login
tsmacdonald          ] https <      0KB     0KB/s |                            
timmy@macpherson:~$ cd pyctactoe/
timmy@macpherson:~/pyctactoe$ cd pttgames/
timmy@macpherson:~/pyctactoe/pttgames$ ls #Note presence of `go`
connect4  go  __init__.py  __init__.pyc  tictactoe
timmy@macpherson:~/pyctactoe/pttgames$ cd ..
timmy@macpherson:~/pyctactoe$ bzr add
ignored 2 file(s).
If you wish to add ignored files, please add them explicitly by name. ("bzr ignored" gives a list)
timmy@macpherson:~/pyctactoe$ bzr ignored #Not go-related
pttengine.pyc                                      *.py[co]
pttgames/__init__.pyc                              *.py[co]
timmy@macpherson:~/pyctactoe$ bzr commit -m "PycTacGo .1"
Committing to: /home/timmy/pyctactoe/                                          
aborting commit write group: PointlessCommit(No changes to commit)
bzr: ERROR: No changes to commit. Use --unchanged to commit anyhow.
timmy@macpherson:~/pyctactoe$ bzr commit -m "PycTacGo .1" --unchanged #Remember how we agreed that I added the go folder (a change)?
Committing to: /home/timmy/pyctactoe/                                          
Committed revision 65.
timmy@macpherson:~/pyctactoe$ bzr push lp:~tsmacdonald/pyctactoe/pyctacgo #Note: I deleted the branch right before this. So it's a new start.
Permission denied (publickey). <      0KB     0KB/s |                          
bzr: ERROR: Connection closed: please check connectivity and permissions       
timmy@macpherson:~/pyctactoe$ 

```

So I gather that there's something wrong with my key, which I don't understand since I added it in exactly the same way I did with my old computer (and for simplicity I deleted that key from my account). And I also don't understand what's going on with the "no changes to commit" message, which I've been receiving on both computers.

Thanks for the help, and I'm sorry that this is turning out much more complicated than it should. If anyone here is thinking, "This is ridiculous. RTFM." then please direct me to a FM to R. I've looked at the Launchpad help but they don't seem to have much troubleshooting information, and the man page itself is overcomplicated and less helpful than you might think.

---

