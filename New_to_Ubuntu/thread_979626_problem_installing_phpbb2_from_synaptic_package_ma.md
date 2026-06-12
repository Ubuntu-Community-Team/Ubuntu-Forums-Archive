---
title: "problem installing phpbb2 from synaptic package manager"
date: 2008-11-12
forum: New to Ubuntu
---

### Post by shanep-server on 2008-11-12
I installed Lamp. Then i tried to install phpbb2 from the synaptic package manager. From here I was prompted to create, populate, none. I opted for populate. I was never asked for my mysql root password or given an option of which database to populate. I went threw with the install and reinstalled phpbb2. This time I tried the create database option. Here I was presented with a prompt to enter my mysql root password. I proceeded. I was told in and error that there were no new tables created. 

I was curious if anyone has had this sort of problem. Or what you might have for suggestions on this matter. It did create /usr/share/phpbb2/ but what do i do with this if phpbb2 didn't create tables in my database?

Any help would be great

---

### Post by longtex on 2009-05-20
Did you ever get it working? 

I have more or less the same problem. I don't think it ever asked for the mysql password, and it failed at trying to add a field to the table phpbb_sessions_keys --- actually, it hangs, and I have to go kill it. It's also stuck in the queue in synaptic, so it goes through this crap each time I try to add anything. No doubt it can be removed from synaptic, but I keep thinking something will break loose and it'll finally solicit the root password and run... fortunately (?) I haven't gotten to the point where I actually NEED phpbb, just yet.

---

### Post by longtex on 2009-05-20
But it just keeps getting better. Reminds me of an old song by the Flatlanders (Joe Ely, Jimmy Dale Gilmore, Butch Hancock) that has a line in it that goes something like "The poor old fool, he's out on the track, he can't go forward and he can't go back..." 'cause that's where I am with phpbb2 and synaptic. When I try to remove it, it throws an error in the postremoval script (guessing it has something to do with the mysql database, butt who nose?) but it shows as not installed; then when I try to install it, it throws an error in the post-install script... 

Any ideas?

---

