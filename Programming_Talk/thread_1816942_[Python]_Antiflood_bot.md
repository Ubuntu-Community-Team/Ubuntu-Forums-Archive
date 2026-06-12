---
title: "[Python] Antiflood bot?"
date: 2011-08-02
forum: Programming Talk
---

### Post by ryuguns on 2011-08-02
Alright, I'm writing a bot for an IRC chat in Python. I wanna add an antiflood feature, for example, if someone sent over 10 messages in one second, kick them. But, the bot will have other features, I'm stuck on solving that. Any suggestions?

I thought about using threading by the way, it isn't something I used before, so I don't know if/how I should use that.

---

### Post by Bachstelze on 2011-08-02
You could have a [queue](http://en.wikipedia.org/wiki/Queue_%28data_structure%29) of the last 9 messages received from a user. Then when the bot recieves a message from that user, it checks whether the last message in the queue was recieved over one second ago. If so, it pops the oldest message from the queue and pushes the new message onto it, if not it kicks the user.

---

### Post by ryuguns on 2011-08-02
Thanks, that is a great solution, will use it :D.

---

