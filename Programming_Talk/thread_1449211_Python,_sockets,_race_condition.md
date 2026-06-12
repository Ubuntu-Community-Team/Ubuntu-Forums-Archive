---
title: "Python, sockets, race condition???"
date: 2010-04-07
forum: Programming Talk
---

### Post by s1ightcrazed on 2010-04-07
Greetings, I have a client/server socket application that does some database queries. Odd thing happened today - I had a 'print' statement on the client side that I removed, and I began getting errors on one of my socket.recv(buf) statements. I put the print back in, and viola, it started working again. 

I believe that I am bumping into a race condition, but I'm not positive, and if I am then I can't figure a way around it. 

On the server side, I receive the name of a database table, open a cursor, and then loop through the rows. For each row, I do 2 socket.send commands, the first being the size of the row, and the second is the actual row itself. When we're out of rows I send a specific message that I test for on the client side. 

On the client site I have a while loop that does 2 socket.recv calls. The first gets the size, and the second gets the row, using the size reported in the previous recv as the buffer size. 

All of this works fine, but only because I have a 'print' in the while loop. 

I.E.:

```
while 1:
        line_len=socket.recv(13)
        line=socket.recv(int(line_len))
        print line

```

As soon as I take that print out, and replace it with, lets say, a file write, I start getting errors on the "line=socket.recv(int(line_len))" line. 

The error:

ValueError: invalid literal for int() with base 10: "('3/4 YEAR', "

The "('3/4 YEAR', " junk is the end of the previous line. What I think is happening is that I'm whipping around the while loop and hitting the line_len=socket.recv(13) again BEFORE the server has had a chance to prep the DB line, calc the line length, and do its socket.send. In essence, I'm beating it to the punch, and my recv is getting whatever happens to be in the buffer at the time, in this case, a fragment of the previous message. The print takes just enough time to avoid this condition. If I throw a time.sleep(.001) in the while loop, it bypasses the error, just like the print did. 

I have NEVER seen this before. I know I'm not going crazy. 

Any ideas?

---

