---
title: "[SOLVED] Java Read/Write Issues"
date: 2008-04-05
forum: Programming Talk
---

### Post by Griff on 2008-04-05
So I have a file I need to be able to read from and write back to.  It has the following format:
```

10001
111
20002
222

```
I'm trying to test my reader by just printing the above contents to the screen, but the file I want to read just gets overwritten (and left blank) and null is written to screen.  Here's my test code:
```

		try {
			BufferedReader in = new BufferedReader(new FileReader("test"));
			BufferedWriter out = new BufferedWriter(new FileWriter("test"));

			System.out.println(in.readLine());
			System.out.println(in.readLine());

			while ((lineNum = in.readLine()) != null) {

				System.out.println(lineNum);
				
			}

		}
		catch (IOException ex) {
			System.out.println(ex);
		}

```
So 2 null values get printed to the screen. Of course the while loop is not being entered since 'in' is returning a null.
Any help will be greatly appreciated.
--Griff

---

### Post by mike_g on 2008-04-05
Maybe try writing the output to a different file?

---

### Post by Griff on 2008-04-05
> **mike_g said:**
> Maybe try writing the output to a different file?

I didn't actually write to the file up there, I just initialized a buffered writer.  But just in case I did comment the writer out and the same result occurred.

---

### Post by nick_h on 2008-04-05
Try opening the FileWriter in append mode:
```
BufferedWriter out = new BufferedWriter(new FileWriter("test", true));
```

---

### Post by Griff on 2008-04-05
> **nick_h said:**
> Try opening the FileWriter in append mode:
```
BufferedWriter out = new BufferedWriter(new FileWriter("test", true));
```

Nope, I even commented the writer out completely.  Same problem.

What's really bothering me is how a *reader* is *writing* this file. :(

---

### Post by Griff on 2008-04-05
Breakthrough! You were right nick_h.

I forgot to uh...re-enter the contents of the file from the last test so it was still empty when I ran the test with your suggestion.  No wonder I was printing nulls!  The append option seems to just write after the end of the data that was already in the file.

I'll actually need to rewrite data in the file so how can I go about this?  I'd like to just be able to overwrite one line.

---

### Post by nick_h on 2008-04-05
Yes.  The append option appends to the end of the file.  The other option is to overwrite the file.

---

### Post by Griff on 2008-04-05
Is there any way to traverse the file down without overwriting the contents.  I know what line I need to overwrite.  Any ideas?

---

### Post by Griff on 2008-04-05
I figured out what I want to do.  Thanks for all the help!

-Griff

---

### Post by HaRLo on 2008-08-13
I'm facing this problem too. I'm wondering why the file content become blank and not even going to while loop. Can anyone tell me? Thanks much

---

### Post by Reiger on 2008-08-13
The reason why the loop isn't entered should be clear to you (content = null -> exit the loop) ... But. Ever tried working with FileInputStream & FileOutputStream? (I already provided a code sample for the InputStream version once...) 

Those will give you C-like flexibility (it's got its own fseek() etc. functions) ...

---

### Post by Belerophon on 2008-08-13
> **HaRLo said:**
> I'm facing this problem too. I'm wondering why the file content become blank and not even going to while loop. Can anyone tell me? Thanks much

The thing is that as the reader and writer are created at the same time it makes things bad lol.
So when you create the reader, there's no problem;
Next you create a writer. But this writer is NOT in append mode, so the it "blanks" the file....
Next you try to read....a blank file!


So you should really create the writer only after creating and using the reader...

Hope this helps.

EDIT:
this simple change should work...
```
try {
			BufferedReader in = new BufferedReader(new FileReader("test"));
			

			System.out.println(in.readLine());
			System.out.println(in.readLine());

                       
			while ((lineNum = in.readLine()) != null) {

				System.out.println(lineNum);
				
			}
                        BufferedWriter out = new BufferedWriter(new FileWriter("test"));

		}
		catch (IOException ex) {
			System.out.println(ex);
		}
```

---

### Post by HaRLo on 2008-08-13
> **Belerophon said:**
> The thing is that as the reader and writer are created at the same time it makes things bad lol.
So when you create the reader, there's no problem;
Next you create a writer. [COLOR="DarkOrange"]But this writer is NOT in append mode[/COLOR], so the it "blanks" the file....
Next you try to read....a blank file!

So you should really create the writer only after creating and using the reader...



Hello Thanks for explaining my question but i'm still have a bit confusing regarding the highlighted sentence. What do you mean by not in append mode and it "blanks" the file? Since it is not in append mode, what is the default mode cause it "blanks" the file?

Because i thought it can write data into the file after the file has been read

---

### Post by Reiger on 2008-08-14
Read the API tutorials of SUN and you'll know why: it specifically mentions that unless in append mode the writer will erase a file *before* writing to it...

And that little piece of behaviour -which is great all by itself- killed your app.

---

### Post by Belerophon on 2008-08-14
...exactly like Reiger said...
read this page,the "constructor summary" (actually, whenever you have doubts about any given method or class from java api, just go to the java API pages, or type "<method | class | etc> java" in google) :
[http://java.sun.com/j2se/1.4.2/docs/api/java/io/FileWriter.html](http://java.sun.com/j2se/1.4.2/docs/api/java/io/FileWriter.html)


```
Because i thought it can write data into the file after the file has been read
```
You really can! You should just be careful with the "moments" when you create the objects for reading and writing...
 
I'm not trying to say you shouldn't post here your doubts, but you should primarily search in the java API pages and read for yourself which is the behaviour of any given "thing"...if you still have doubts...well, there's a lot of people in these forums who will certainly answer you ;).
This way, you'll certainly find your answers much quicker!

---

### Post by HaRLo on 2008-08-21
Thanks to Reiger and Belerophon providing solution.Now I'm finally understand after testing in few days. Thanks very much

---

