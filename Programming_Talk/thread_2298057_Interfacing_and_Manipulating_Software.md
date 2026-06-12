---
title: "Interfacing and Manipulating Software"
date: 2015-10-08
forum: Programming Talk
---

### Post by mike-ratcliff on 2015-10-08
Hello there!

Please bare with me I may over explain this.

Many years ago in the dark ages when I used Microsoft Windows XP I used to play a little game with my friends called Tibia, a sort of online RPG. A very clever person wrote some software which allowed you to pull data from the game client - Player stats (Health points, skill levels, experience, things like that) basically any text value which was displayed on the screen, nothing sent from the server just what was stored in memory. I think it had something to do with hex value from the executable.

I am curious if something like this is possible with Linux applications, I understand that is a very vague description and includes all sorts of software written in all sorts of languages. Everything above is now irrelevant.

I have been talking with a friend on Skype tonight and his internet keeps disconnecting so the call gets terminated.  I am curious if it is possible to write a piece of software which can pull information from Skype (like I explained above, somewhat terribly), check who is calling and automatically answer. Maybe some one can offer an insight please?

I guess what I am after is a Skype API and a simple Google search would give me an answer.


Look forward to your thoughts.


Thanks,
Mike

---

### Post by tgalati4 on 2015-10-08
If you know the skype packet protocol, you can use *tcpdump* or *wireshark* and simply grab the skype packets and decipher them.  So, yes it is possible to intercept skype packets and then automatically reply to a skype phone call.

Let us know if you find the skype protocol.

---

