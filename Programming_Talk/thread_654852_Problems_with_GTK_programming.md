---
title: "Problems with GTK programming"
date: 2007-12-31
forum: Programming Talk
---

### Post by mellowswng on 2007-12-31
Hello , 
I am developing a network application (in C )  as a project for school and appear to have some problems with programming the UI for the client with GTK , i have just begun learning GTK ... anyway the problem is that I can't find a way to constantly read from my socket connected to the server without freezing the application window.... clicking some buttons in my app. sends direct commands to the server and waits for reply to then act correspondingly ... but some events aren't that synchronized  and so the client has to read all the time what's new from the server ... this would have to be something to be done in the background .... The only idea i came up with was to separate the interface from the  actual client in another C program ( child for the interface program ) and to redirect the output of it to the interface program ... also when i need to send something to the server i call a signal for the child to read what's in a pipe / fifo .... but that seems like a long way around for something that I think must be done much more easy ... 

Thanks in advance.

---

### Post by kripkenstein on 2007-12-31
I think that what you are looking for is programming with threads.

In general terms, you would have a thread for the GUI, and a thread for the socket activity. The two threads work in parallel, so the GUI is always responsive. Basically all well-written GUI programs do something like this.

However, it is a bit tricky, since the threads need to communicate, and this is not trivial. You can easily get data corruption issues (if both threads work on the same data at the same time). To solve this there are locks, mutexes, and such. You might want to read a tutorial on threading for this sort of stuff.

However, perhaps there is an easier way to do your specific program. If all it does is a single button and a single type of socket command, then perhaps you can do the socket in a separate program, like you say (run with a non-blocking shell command). This might work. It is like the threads solution, but less flexible. Perhaps easier for a simple app though.

---

### Post by mellowswng on 2007-12-31
The app. is really simple, in the sense it's just to check more the knowledge in network socket programming ... it's a simple tictactoe game with a protocol defined by myself ... 

    I use simple buttons for the   3x3 table the problem is when i have to receive moves made by the other player . I don't know when i will receive a move  for sure ... so  for example if player 1 clicks a box it is checked by the server if it is valid ... receives a validation (the move itself with some parameters ) and sets the label accordingly ... the bad thing is i can't wait for the other move (by the opponent) while the user clicks a box ...  I know I will have to wait for one but waiting in any interface event handler would freeze it ... 

   I will try some things you suggested if I can't come up with anything  more simple :) 

Thanks,
and Happy New Year!

---

