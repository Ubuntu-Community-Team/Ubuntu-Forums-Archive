---
title: "ftp server using socket programming"
date: 2010-02-19
forum: Programming Talk
---

### Post by sashar on 2010-02-19
i am implementing an ftp server using socket programming. For sending the files i am opening the files in the binary mode and then sending the data in them byte by byte. The problem is that when i send some audio file, it gets transferred but with very poor quality. Initially i was sending many bytes at a time, then i reduced the block size to 1 byte per block, but still i am not getting the desired quality of audio.....can anybody please help me..

---

### Post by era86 on 2010-02-19
I don't know if the quality of audio is affected by the block size of transfer.  If you are reading in the data as is, it should be reproduced on the client side with the same attributes unless you modify the bytes some how during transfer.

What language are you using?  I wrote an audio streamer in Python awhile back but the concepts might be the same.

---

### Post by Zugzwang on 2010-02-19
@OP: Something as a "FTP server should transfer a file 1-to-1, so no changes in the file should occur. So first of all, check if the file was really transferred correctly. If not, have a look what's wrong. Is the transferred file too small? Are 0x00-bytes transferred incorrectly?

---

### Post by sashar on 2010-02-19
First of all...thanks for the replies....
i am not doing anything with the block of data....i am using c language......When i check the size of the file at the client it is of the same size as at the server.
one more thing which amazes me is that if i run the client program on the same system on which server is running, the file gets transferred perfectly i.e with original quality.
so the only difference i can think of in the two cases is that of a LAN wire coming in between the system....i dont know why should that make any difference to program output...

---

### Post by dwhitney67 on 2010-02-19
sashar -

Can you please define what you mean by "quality" (of audio)?  You have used this term twice.

Are you saying that the playback of the MP3 file sounds better on the original machine versus when played on the receiving machine?

Aside from different sound card and/or speakers, I suppose it is possible the files could contain different data, but that is unlikely (unless you did not transfer the file correctly).

Use the 'md5sum' utility on each file; compare the results:
```

md5sum *filename*.mp3

```

---

### Post by Zugzwang on 2010-02-19
The data transmitted shouldn't change. However, it might come in blocks of different size than if both programs run of the same computer. So you don't ignore the return value of the "recv" call, right? 

One quick thing to check if "valgrind --tool=memcheck <yourclient>" complains about using uninitialized data. The same can be done with the server.

---

### Post by sashar on 2010-02-19
@dwhitney67: by quality i meant that the file played better when client is on the same system. I am getting different results when using md5sum utility on the original file and the received file even in the case when the client is on the same system though the file in this case sounds normal.

@Zugzwang: i am sending data by sending it through blocks of fixed size. for eg. if i have a file of 2050 bytes, i have fixed my block size as 1024 bytes...so i am sending 2 blocks of 1024 bytes and i block of 2 bytes. i am using write and read functions for writing and reading from the socket respectively...

---

### Post by Some Penguin on 2010-02-19
Are you checking whether you actually received or wrote as many bytes as you wanted to?

---

### Post by sashar on 2010-02-19
@some penguin: the size of the file received at the client is same as that at the server. 
my steps for implementing the ftp server were like this:
1. sent complete file in one go i.e size of the block =size of the file to be sent. this created a lot of problem. The program was not able to send even a txt file successfully across systems.

2. divided file into blocks of size 1024 and one block of size=remainder of filesize divided by 1024. in this case text file went successfully with no data loss. complete audio file reached at the client but with bad quality

3. sent the file byte by byte. txt file successfull, pdf file successful, audio file transferred successfully but with not much improvement in sound quality.

---

### Post by Some Penguin on 2010-02-19
What I was getting at is that read() and write() calls don't have to actually read and transmit everything you want them to  -- they can transfer less, which is why you have to check the return value.

---

### Post by gmargo on 2010-02-19
> **sashar said:**
> the size of the file received at the client is same as that at the server. 

That tells you little.  Is the file content the same?  Run an "**md5sum -b filename**" on both ends.

You are most likely either a) not actually using binary mode, or b) confused about network byte order somewhere in your code and hence are switching bytes around.  It's mighty difficult for us to help you debug mystery code.

---

### Post by sashar on 2010-02-20
thanks for the replies people...my problem is now solved. The size of the files received seemed to be same but when i saw the size through properties menu, i saw that there was some extra bytes in the received file.This was the reason why the received file was not playing correctly. That was due to some error in the code...but that is now resolved......thanks again people.......

---

