---
title: "Mono/C# IM Client (WIP)"
date: 2008-05-26
forum: Programming Talk
---

### Post by klange on 2008-05-26
About two years ago when I was still on Windows I wrote up an IM client/server with my own little protocol. I wrote the first client in VB.NET, and it was pretty nice. I wrote a few more mini-clients in Python, Java, and even half of a client in PHP. I've been putting off a true Linux port with all the bells and whistles until now. Finally decided I'd re-write the original client natively. I still don't know enough C or PyGTK to get the job done there, so I've turned to Mono (I also promised a long time ago I'd rewrite the thing in C# :) )
I had to relive the nightmares of "managed" multithreading, but I got through it.

[[img]http://random.ogunderground.com/pandemic/thumbs/WorksForMe.png[/img]](http://random.ogunderground.com/pandemic/WorksForMe.png)

There are still some things to do to get it up-to-scratch with the protocol and as a basic client. Unfortunately, MonoDevelop's GTK code generation tools don't like Toolbars, so I have a row of buttons which doesn't look good. I'll get that fixed by manually writing the code for a Toolbar.

Anyway, the primary reason why I'm posting here is to get some ideas for features. My protocol already supports the basics - formatting (despite the lack thereof in the picture), status, profiles, avatars, chat rooms, file transfer (via FTP), and invites. I already have plans to add server-side friends lists.

So, if you have any features you want to see in an IM client/protocol, post them here and I'll see what I can do.

---

### Post by Quikee on 2008-05-27
Audio and Video support :)

---

### Post by slavik on 2008-05-27
docs, lots of docs. :) (mainly the protocol)

---

### Post by Lau_of_DK on 2008-05-27
Great project! :) I look forward to seeing what you'll come up with.

One of the things I'm really missing with the MSN protocol is turbo-charged transfer. Optimally you would have a bandwidth throttle in the transfer Window, so you could dedicate anything from 1 -> 100% of your bandwidth. For some reason my MSN wont exceed 2.5 kb/s....? :)

Its idea, hope you can use it.
/Lau

---

### Post by klange on 2008-05-27
Thanks for the suggestions. I'm definitely going to look into video chat, it would be a valuable feature, especially when Pidgin doesn't even have it. Data transfer throttle should be simple enough, but it'll take a change in the way file transfer operates (right now it's a c->s->c FTP transfer, which is horribly slow and inefficient). I'll probably keep the old method in there for backwards compatibility and add a new direct point-to-point transfer system as well.

I'm trying to keep things as well documented and straight forward as possible when writing the code. I'm also doing my best to submit documentation on some of the .NET functions that aren't yet documented in Mono (but my confirmation email never arrived - never even hit my SMTP server - so I can't yet upload my additions)

---

### Post by Lau_of_DK on 2008-05-27
Its interesting to look at how the MSN protocol handles file-transfers. If I remember correctly then first you send a payload which lets the recipient know that there's a file coming his way. If he chooses to accept it, you send a request for an IP, which comes back with the recipients IP adress. But despite this direct approach, its still awfully slow.

Nevermind - The way of getting the IP is good, making a full-bandwidth transfer shouldn't be a problem. 

Good luck with it,
Lau

---

### Post by klange on 2008-05-31
What's the deal with the GtkTextView/Buffer? Why don't they have a built in export method of any sort? That's so cruel.

Anyway, [here's](http://pandemic.oasis-games.com/shots/wysiwyg.png) the WYSIWYG message editor showing my formatting tags. I wrote a simple processing script to output HTML using tag names. When closing tags, it cuts them off at the first space to properly process links. Images are handled in a different way in a TextBuffer than standard formatting, and I haven't looked at it yet.

To show my progress, here's a list of things I have done:
**Friends list**
- Does not process any sort of actual list, but will display friends as units. Need to make this more "list-like"
**Conversation Window**
- Gecko HTML rendering that automatically scrolls down for display messages.
- WYSIWYG message editor with keyboard shortcuts.
**Pandemic Backend**
- Implemented full UDP socket subsystem
- Safe multithreading using GTK invoke.
- Implements protocol messages: Handshake (10), login (1), logout (4), message (2), chatrooom (11, 12, 13, 14)
**Tray Icon**
- Hides/shows friends list on click.
- Right click menu (currently only has "quit")

And the short-term future goals (IE, this weekend):
**Friends List**:
- Actually list friends.
- Right click menu -> Start Convo, Invite to Chat, etc.
- Double click -> Start Convo
- Properly display avatars from remote users.
**Conversation Window**:
- Actually refresh a newly created window if it was opened because of a new message.
- Implement message size safety ("Your message is too long", etc.)
- Chatroom user list.
**Pandemic Backend**:
- Implement conversation invitation messages
**Tray Icon**:
- Add complete right click menu.
**General**:
- Implement login widget (currently hard-coded to login to "TestAccount")
- Implement profile editor.

[img]http://pandemic.oasis-games.com/shots/friends.png[/img]
^ Here's an updated friends list using some formatted text in a TreeView. Though I use markup on the name, causing it to not be searchable, I used a hidden column containing only the plaintext username that is used for searching. I've been looking everywhere for how to remove the left margin - no luck so far. Right click menus work great after I overrode the standard button event.

---

### Post by klange on 2008-06-01
Some small updates. Friends list now looks up a set of friends (currently stored in a file, obviously not the way to go for the pre-alpha release). I'll be adding a login system today so that I can get it ready for testing.

[[img]http://random.ogunderground.com/workstation/anytime/thumbs/NowWithMorePandemic.png[/img]](http://random.ogunderground.com/workstation/anytime/NowWithMorePandemic.png)

---

### Post by Lau_of_DK on 2008-06-01
> **WindowsSucks said:**
> Some small updates. Friends list now looks up a set of friends (currently stored in a file, obviously not the way to go for the pre-alpha release). I'll be adding a login system today so that I can get it ready for testing.

[[img]http://random.ogunderground.com/workstation/anytime/thumbs/NowWithMorePandemic.png[/img]](http://random.ogunderground.com/workstation/anytime/NowWithMorePandemic.png)

Man that looks good, I cant wait till you go Alpha!

Finally a guy who appreciates a fine looking GUI :)

/Lau

---

### Post by klange on 2008-06-01
Switch from a TreeStore to a ListStore and now [everything is working right](http://pandemic.oasis-games.com/shots/liststore.png).
Also implemented a queue and moved the byte[]->string processing into the receiving thread. The queue ensures that everything is acted on at some point, in case the Invoke() is late. The chat room uses a VPaned to hold the Gecko renderer and the user list.

---

### Post by Retrospekt on 2008-06-05
Looking awesome man.  :D

---

