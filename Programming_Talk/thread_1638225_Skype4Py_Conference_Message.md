---
title: "Skype4Py Conference Message"
date: 2010-12-05
forum: Programming Talk
---

### Post by urwaldfloh on 2010-12-05
Hello!


I discovered Skype4Py and I'm trying to simplify my work. I want to send a message to an existing conference chat, but i don't know how to do it. I can send to a single person, but i don't know how to send to group of people in a chat.
I'm sure it's pretty easy, but I don't get it.

Thanks, Bernd

---

### Post by urwaldfloh on 2010-12-08
anybody? :-(

---

### Post by urwaldfloh on 2010-12-09
done

---

### Post by Roni L on 2011-02-08
> **urwaldfloh said:**
> Hello!


I discovered Skype4Py and I'm trying to simplify my work. I want to send a message to an existing conference chat, but i don't know how to do it. I can send to a single person, but i don't know how to send to group of people in a chat.
I'm sure it's pretty easy, but I don't get it.

Thanks, Bernd

I have the same problem. How did you solve that?[COLOR=#000000][/COLOR]
[CENTER][COLOR=#000000] 
[/COLOR][/CENTER]

---

### Post by Asday on 2011-02-08
I did some work with this a while ago, and I can't for the life of me remember how I did it.  When I get home, I'll trawl through a silly little script I made, and see if it helps.

---

### Post by Roni L on 2011-02-16
> **Asday said:**
> I did some work with this a while ago, and I can't for the life of me remember how I did it.  When I get home, I'll trawl through a silly little script I made, and see if it helps.

On a long trip? :-D It would be very nice to see your script.

---

### Post by Asday on 2011-02-16
> **Roni L said:**
> On a long trip? :-D It would be very nice to see your script.

Hahaha oh god I'm so sorry, I forgot about this thread so hard.  Here's my awful raw coding, likely commentless, 1 letter variables, one-liners, gotos, etc.  (I don't do things tidily left to myself.)  >_<

(After looking at the code):  On second thoughts, I'm not going to post it.  Jesus gods, why did I use that naming convention?

Let's try and work out what I did and how.

[PHP]import Skype4Py as sky #why do people insist on using capital letters?
cl = sky.Skype() #cl is client
cl.Attach()
conf = cl.Conferences # returns a list-like object
#Then this is where I get stuck
# You can get the Ids of conference conversations with for i in xrange(len(conf)): print(conf[i],i)
# Now I'm looking for a way to get a list of participants with an id.  Gimme a while.
#Ok, so conf[i].Calls is another list-like object, and each item in it has a .Participants list.
# I'm trying to find one somewhere that is of non-zero length,
# but to be honest, I'm getting lost in all the nested stuff.
# So far, we have cl.Conferences[x].Calls[y].Participants[z][/PHP]

Wow, I'm utterly lost with conferences.

It seems that conference chats aren't distinguished from normal chats.

[PHP]chats = cl.ActiveChats[0]
for i in chats:
    for l in i:
        print(l,i)[/PHP]
Prints out a load of Skype4Py.user.Users.  Also, you can send stuff with:

[PHP]i.SendMessage("Fish")[/PHP]

Hopefully with this you should be able to get the right conference, and send a message to it.

If not, I could prototype it for you, complete with proper structure and comments, and see if it helps.

---

### Post by coolness on 2011-02-25
Hey, please could you make that a bit more newbie-friendly? I'm getting OK at python slowly, but i didn't understand your example, nor did it work when trying to copy-paste your stuff into a script. So, how can i actually send group messages?

Many thanks.

---

### Post by Asday on 2011-03-04
I'm actually quite against just copypasting code, as I went through a long patch of doing pretty much nothing but that with VB.NET, and ended up learning exactly 0.

You need to attach Skype4Py to your Skype client, get a list of chats (of which chats and conferences are not distinguished), then figure out which ones are conferences, likely through checking to see how many members a chat has.

To send a message to a specific chat, probably the easiest way to choose one, is to pull out usernames of participants, and send one based on those.

This should all be achievable with Python fundamentals, along with:

[PHP]import Skype4Py as sky
client = sky.Skype() # Client instance
client.Attach() # I think this allows you to use the client.  Whatever, it's required.
client.ActiveChats[0] # I believe this is a list-like object of all active chats.  Can't remember why the index is there, but it's likely important.
#and finally
Skype.Chat.SendMessage(str) # the Skype.Chat is some object or other, you'll find a list of them in ActiveChats[0].  SendMessage sends a message.[/PHP]

---

