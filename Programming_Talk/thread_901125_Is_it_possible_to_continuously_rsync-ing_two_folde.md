---
title: "Is it possible to continuously rsync-ing two folders?"
date: 2008-08-26
forum: Programming Talk
---

### Post by CyberAngel on 2008-08-26
Hi,

I have a client and a server. The client is collecting some data every second that I want them to be sent to the server in real time (so a cron job for periodically syncing the folders is not fitting my needs).

Is it possible to use rsync from the server, to continuously retrieving the collected data from the client and then deleting the data from the client if they have been retrieved correctly?

Thanks,
Vangelis.

---

### Post by dsm iv tr on 2008-08-26
You could just write a bash script with a while loop to run rsync constantly on the server end - your very own "daemon".

```

#!/bin/sh

while true ; do
     echo "rsync command would go here"
     sleep 1 # or however many seconds you like
done

```

```

$ nice -n5 *script_filename* &

```

---

### Post by CyberAngel on 2008-08-26
> **dsm iv tr said:**
> You could just write a bash script with a while loop to run rsync constantly on the server end - your very own "daemon".

```

#!/bin/sh

while true ; do
     echo "rsync command would go here"
     sleep 1 # or however many seconds you like
done

```

```

$ nice -n5 *script_filename* &

```

I was thinking of something like this, but I was also thinking of some other aspects like if we lose the link for a while what happens then?

Anyway I don`t think there will be a problem. I`ll try it :)

Thanks for the reply in any case!

---

