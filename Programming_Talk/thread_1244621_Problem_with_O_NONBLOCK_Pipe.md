---
title: "Problem with O_NONBLOCK Pipe"
date: 2009-08-19
forum: Programming Talk
---

### Post by hosseinyounesi on 2009-08-19
Hi,
I'm trying to send and receive using pipes:

send.cpp
```

struct
    {
            long a;
            long b;
    }T;
cout << "1" << endl;
if ( access ( FIFO_NAME, F_OK ) == -1 ) {
            res = mkfifo ( FIFO_NAME, 0755 );
            if ( res != 0 )
                    cout << " Can't make fifo" << endl;
}

cout << "2" << endl;
pipe_fd = open ( FIFO_NAME, O_WRONLY);
cout << "3: " << pipe_fd << endl;
a=b=1;
res = write ( pipe_fd, &T, sizeof ( T ) );
cout << "4" << endl;
close(pipe_fd);

```

recv.cpp
```

cout << "1" << endl;
pipe_fd = open(FIFO_NAME, O_RDONLY | O_NONBLOCK);
cout << "2" << endl;
res = read(pipe_fd, &T, sizeof(T));
cout << T.a << T.b << endl;
close(pipe_fd);

```

```

./send
./recv

```

open is correct, but when send.cpp executes "write" the program terminates and "4" is not displayed!!!! I recv side the T.a and T.b are not correct !

What's wrong with my programs?! (I have to say that programs are working correct when I remove O_NONBLOCK flag)

thanks

---

### Post by uljanow on 2009-08-19
if you try to read from a pipe whose write end has been closed, read returns 0 to indicate eof.

---

### Post by soltanis on 2009-08-19
On the writer side, check the return value of the write operation, because write says in the documentation that it may write UP TO the number of bytes you asked it to, but it may write less (or none at all). If nothing is being written in the first place, it makes sense that the reader is EOF'ing before reading anything at all.

If the resultant is < 0, then an error has occurred, as I think is what is happening in your program; throw in a perror call to see what the problem is.

---

