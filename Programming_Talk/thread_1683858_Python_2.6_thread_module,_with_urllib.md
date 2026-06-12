---
title: "Python 2.6 thread module, with urllib"
date: 2011-02-08
forum: Programming Talk
---

### Post by Asday on 2011-02-08
I've been poking about with threads for my first time, and came up with something that seems to work nicely, and not be horrid, as follows:

[PHP]import thread
import os
import urllib
import tempfile

def downloader(string_download, dict_return, int_retries = 5, string_path = False):
    if string_path:
        file_download = file(string_path +
                             string_download.split("/")[-1], "wb")
        errors = 0
        while True:
            try:
                file_temp = tempfile.NamedTemporaryFile("r+b")
                file_http = urllib.urlopen(string_download)
                file_temp.write(file_http.read())
                endpos = file_temp.tell()
                file_temp.seek(0)
                file_download.write(file_temp.read(endpos))
                file_download.close()
                file_temp.close()
                break #Not reached if urlerror
            except:
                errors += 1
                if errors == int_retries:
                    dict_return[string_download] = False
    else:
        errors = 0
        while True:
            try:
                file_temp = tempfile.NamedTemporaryFile("r+b")
                file_temp.write(urllib.urlopen(string_download).read())
                endpos = file_temp.tell()
                file_temp.seek(0)
                dict_return[string_download] = file_temp.read(endpos)
                file_temp.close()
                break #Also not reached if urlerror
            except:
                errors += 1
                if errors == int_retries:
                    dict_return[string_download] = False
                    break[/PHP]

Ignoring the lines >80 characters long, and general lack of finesse or comments, I thought it was fairly good.  If I call it in some sort of loop it works nicely, for instance:
[PHP]a=["www.google.com","www.bing.com","www.yahoo.com"]
b={}
for i in a:
    thread.start_new_thread(downloader, (i,b))[/PHP]And I get some fillings in b, and it all looks nice.

The thing is, I read this post on stackoverflow, on code quite similar to mine:

> -1 for threads and suggesting the thread module and not doing any locking or even using the Queue module. You're just going to add way more complexity and locking overhead for no gain if you use threads. Even if this wasn't true, your code demonstrates that you don't really know how to use threads. –

And it worried me, 'cause mine works fine, and I like it.

(The code in question did some weird global variable messing instead of passing in the dictionary to "return" to, but apart from that, very similar.)

Should I be worried?

---

### Post by Asday on 2011-02-10
Bump for terror.

---

### Post by MadCow108 on 2011-02-10
I am not very experienced with python multithreading, so following may be wrong:

your code is not threadsafe, all threads update the same dictionary b and as far as I can tell dictionaries are not designed to be used by multiple threads in parallel
you need to add a lock on the updating of the dictionary or use a separate dictionary for each thread

as stated in stackoverflow you are better of using Queue to synchronize the data between the threads.
Queue's are designed to be updated and read by multiple threads.

you should also check if urllib.urlopen is threadsafe.
If not you must lock there too.

also you should reduce the code duplication.

---

### Post by Asday on 2011-02-10
> **MadCow108 said:**
> I am not very experienced with python multithreading, so following may be wrong:

your code is not threadsafe, all threads update the same dictionary b and as far as I can tell dictionaries are not designed to be used by multiple threads in parallel
you need to add a lock on the updating of the dictionary or use a separate dictionary for each thread

None of the data seems messed up, though, I think 'cause I'm writing to different keys every time; it'd only try and write to the same key if there were duplicates, and for proper use, I'd check for that.

> as stated in stackoverflow you are better of using Queue to synchronize the data between the threads.
Queue's are designed to be updated and read by multiple threads.

As mentioned above, though, dict() seems to work flawlessly, and implementing a Queue would be extra work, more overheads, etc.

> you should also check if urllib.urlopen is threadsafe.
If not you must lock there too.[http://mail.python.org/pipermail/python-list/2002-June/147057.html](http://mail.python.org/pipermail/python-list/2002-June/147057.html)

That says it is, but very briefly, and in 2002.  Is there an particularly easy way to find out myself?

> also you should reduce the code duplication.

Yeah :oops:  The code I posted was written in two different locations, and I just copypasted, and ran a couple tests.  It works, but when I put it in something, it'll be neater.

---

### Post by MadCow108 on 2011-02-10
> **Asday said:**
> None of the data seems messed up, though, I think 'cause I'm writing to different keys every time; it'd only try and write to the same key if there were duplicates, and for proper use, I'd check for that.

As mentioned above, though, dict() seems to work flawlessly, and implementing a Queue would be extra work, more overheads, etc.

Did a little reading on python threading.
It works because of two points:
- your threads execute with significant different speeds (http transfer is sloooow compared to cpu) so the chance that the threads overlap on the dictionary access is very very low.
- the python global interpreter lock (GIL). This lock protects the complete object space so parallel access to the dictionary is not allowed and it cannot get corrupted like this.

This means the code should be ok as long as the dictionary key of each thread is unique.
But it is still not very good coding. Who knows maybe someday the GIL is relaxed and your code can fail.

> 
[http://mail.python.org/pipermail/python-list/2002-June/147057.html](http://mail.python.org/pipermail/python-list/2002-June/147057.html)

That says it is, but very briefly, and in 2002.  Is there an particularly easy way to find out myself?

unfortunately there is no easy way besides reviewing the complete code.

---

### Post by Asday on 2011-02-10
> **MadCow108 said:**
> Did a little reading on python threading.
It works because of two points:
- your threads execute with significant different speeds (http transfer is sloooow compared to cpu) so the chance that the threads overlap on the dictionary access is very very low.
- the python global interpreter lock (GIL). This lock protects the complete object space so parallel access to the dictionary is not allowed and it cannot get corrupted like this.

This means the code should be ok as long as the dictionary key of each thread is unique.
But it is still not very good coding. Who knows maybe someday the GIL is relaxed and your code can fail.Then I'll implement a Queue.  It's extra work for literally no gain, but this is, after all, a little muckabout practice program, and practice needs perfection.> unfortunately there is no easy way besides reviewing the complete code.Uhh, yeah, I'm not doing that.  :lol:

---

### Post by MadCow108 on 2011-02-10
its not really a lot of extra work...

[PHP]q = Queue.Queue()
a=["www.google.com","www.bing.com","www.yahoo.com"] 
for e in a:
  threading.Thread(target=downloader, args=(e, q))
b = {}
for e in a:
  b.update(q.get())[/PHP]

and change
[PHP]dict_return[string_download] = file_temp.read(endpos)[/PHP]
to
[PHP]q.put({string_download: file_temp.read(endpos)})[/PHP]

---

### Post by Asday on 2011-02-10
I'm actually gonna not read the code in that post, 'cause I enjoy working this stuff out myself.  (It's why most of my code is an utter mess.  Pfffhahaha.)

---

