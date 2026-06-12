---
title: "[Java] I/O a file to pipe"
date: 2009-03-20
forum: Programming Talk
---

### Post by babacan on 2009-03-20
Hello,
I am trying to manage a very simple task: I want to output my java program the file I point, inorder to pipe to a new program.

For example: "java play | mpg123" 

Pipes the input.mp3 to the mpg123 program to play.
Here is the code I wrote but I couldn't manage it to work :(

[PHP]import java.io.*;

class play{

  public static void main(String[] args) {

try{

FileOutputStream fos = new FileOutputStream("input.mp3");
DataOutputStream dos = new DataOutputStream(fos);
dos.write(1000);

    } catch (FileNotFoundException e) {
      e.printStackTrace();
    } catch (IOException e) {
      e.printStackTrace();
    }
}
}

[/PHP]

---

### Post by dacorr on 2009-03-20
would you be able to provide the error it throws?

Dac

---

### Post by babacan on 2009-03-20
> **dacorr said:**
> would you be able to provide the error it throws?

Dac

it doesn't throw any error . I must confess I am not sure if I am using the right libraries to achive the task I want to achieve.

---

### Post by dacorr on 2009-03-20
i think you want to output the results of the java app to a file, is this correct?

---

### Post by babacan on 2009-03-20
> **dacorr said:**
> i think you want to output the results of the java app to a file, is this correct?

I want to output the mp3 file I point, so the program named mpg123 can grab the data and play it (with using pipe at the terminal).

cheers

---

### Post by dacorr on 2009-03-20
the only thing i can see is that i dont see the original file you wish to open being assigned to the FileoutputStream, you need to use datainputstream to read data from a file, i know C++ uses file descriptors.

once the data is read are you planing to put it to a data output stream.

i believe that the main class is only prepared to accept a string.

between input and output are you planning to do anything withit or convert it to somthing else?

does this help?

---

### Post by babacan on 2009-03-20
> **dacorr said:**
> the only thing i can see is that i dont see the original file you wish to open being assigned to the FileoutputStream, you need to use datainputstream to read data from a file, i know C++ uses file descriptors.

once the data is read are you planing to put it to a data output stream.

i believe that the main class is only prepared to accept a string.

between input and output are you planning to do anything withit or convert it to somthing else?

does this help?

Thanks for your assistance, right now I noticed instead of outputting a file, my program simply overwrites the file caldir.mp3 with an empty file. Seems like I am on the wrong track.

---

### Post by issih on 2009-03-20
If you are doing what I think you are, you aren't using pipes correctly.

The unix pipe doesn't pick up data from a file, it takes data from stdout (i.e. the console output.

That is to say that if you do:

```
ls
```

it outputs a file list to the stdout, that is to the terminal window.

you can grab this output and pipe it to another command like grep.

```
ls | grep billy
```

grabs the file list and greps it for billy, at no point is a file involved.

In your example your java program outputs to a file (input.mp3), not to standard output. Consequently the unix pipe never sees that data. Indeed how would the pipe know what file to pick it up from? the only reference to input.mp3 is internal to the java code.

I think what you want to do is have 'play' output the filename you want to pass on to the standard output, i.e.:

```
system.out.println("input.mp3")
```

and then the pipe might pick that up and pass it onto the next command. I'm not at all sure that will actually work from a java process though.

---

### Post by babacan on 2009-03-20
> **issih said:**
> If you are doing what I think you are, you aren't using pipes correctly.

The unix pipe doesn't pick up data from a file, it takes data from stdout (i.e. the console output.

That is to say that if you do:

```
ls
```

it outputs a file list to the stdout, that is to the terminal window.

you can grab this output and pipe it to another command like grep.

```
ls | grep billy
```

grabs the file list and greps it for billy, at no point is a file involved.

In your example your java program outputs to a file (input.mp3), not to standard output. Consequently the unix pipe never sees that data. Indeed how would the pipe know what file to pick it up from? the only reference to input.mp3 is internal to the java code.

I think what you want to do is have 'play' output the filename you want to pass on to the standard output, i.e.:

```
system.out.println("input.mp3")
```

and then the pipe might pick that up and pass it onto the next command. I'm not at all sure that will actually work from a java process though.

Thanks alot for the clarification! I am still a pretty newbie ubuntu user :)

 Actually this is just a part of my task, the whole the program I want to write is a TCP server and client to play a music file from the server at the client (by piping the mp3 to the mpg123) so simply outputting the file location I want to play won't help me, I have to direct the whole mpg3.

Cheers

---

### Post by issih on 2009-03-20
Well in that case I assume you are dealing with the client end at the moment, i.e. the bit receiving the stream and passing it on to mpg123 for playback.

mpg123 can take data from standard in, so outputting the data from the file to standard out and then piping it to mpg123 should work. (note you apparently need to run it as "mpg123 -" to pick up data from stdin)

You'd still need to squirt the data to standard out though, and I don't know think that unix pipes operate concurrently. I think they operate consecutively, so the whole file would be pulled across by the java client app and then passed over wholesale to mpg123. I doubt this is what is wanted.

All in all, I doubt that a pipe is what you are meant to be using here.

EDIT...I think I'm wrong, I think piped applications are run concurrently, so your little client needs to write to standard out, and then pipe that standard out to mpg123

---

