---
title: "java: exceptions and finally clause confusion"
date: 2006-04-27
forum: Programming Talk
---

### Post by ruzle0 on 2006-04-27
Hi,
i'm going through somebooks teaching myself java and have got confused.

i have this code using a JFileChooser to save an object to a file

```
File fChoosen = m_chooser.getSelectedFile();
FileOutputStream fStream = null;
ObjectOutput stream = null;
try{
   fStream = new FileOutputStream(fChoosen);
   stream = new ObjectOutputStream(fStream);
   stream.writeObject(m_avtiveBean);
   fStream.close();
   stream.close();
							
}catch(Exception ex){
	ex.printStackTrace();
	JOptionPane.showMessageDialog(BeanContainer.this, "Error: "+ex.toString(),
	"Warning", JOptionPane.WARNING_MESSAGE);
}finally{
   if(fStream != null) fStream.close();
   if(stream != null) stream.close();
}
```

i wanted to put a finally clause (as above) after the catch, to close the streams in the case of an exception during write, but it complains that the close() method has an uncaught exception. Putting a try catch in the finally clause doesn't sound right to me, can anyone give me any tips

---

### Post by index_0@ya.com on 2006-04-27
thiink u can catch at function start block

public void myFunction throws Exception{ 
      //     do whatever u want !!!
 }

..
 prehaps it can avoid cluttering !

---

### Post by macxek on 2006-04-27
Usually, when you work with streams, sockets, database connections and that sort of things, you should 'think safe'. The usual approach is indeed to put a try/catch clause in the finally, so that it won't crash your app if something goes wrong while closing the stream. Don't worry about your code being a bit cluttered: safety has a price.

Although like index_0 said, you may still add a 'throws [my_exception]' to the method declaration if you want to handle the exception at a higher level. It all depends on the implementation. The drawback to this is that the method could have done it's job successfully but the close() went bad. In that case, if you throw a generic Exception, the method that invokes the method you're working on won't be able to determine what went bad.

Hope this helps!

Cheers

---

### Post by sphinx on 2006-04-27
Actually yeah, it is sometime nessasary to put a try catch block within a catch or finally block. Also, just a small thing, but calling close() on a stream calls close() on any contained stream, at least that should be the case. So I would have written the code thus:

```

File fChoosen = m_chooser.getSelectedFile();
ObjectOutput stream = null;
try{
   stream = new ObjectOutputStream(new FileOutputStream(fChosen));
   stream.writeObject(m_avtiveBean);
}catch(Exception ex){
	ex.printStackTrace(System.err);
	JOptionPane.showMessageDialog(BeanContainer.this, "Error: "+ex.toString(),
	"Warning", JOptionPane.WARNING_MESSAGE);
}finally{
   try {
      if(stream != null) stream.close();
   } catch(IOException ioe) {
      ioe.printStackTrace(System.err);
   }
}

```

You also dont need to close the stream within the try block if you are closing it in the finally block because the finally block is run regardless of there being an exception or not. And another small personal preference of mine is to have the stack traces printed to the error stream (System.err) as this allows you to redirect the error output to a seperate file from the command line if you wish. In the absence of a logging toolkit, of course.

dammit macxek, you've snuck a comment in while I've written mine again! second day in a row! :)

---

### Post by LordHunter317 on 2006-04-27
[QUOTE=ruzle0]i wanted to put a finally clause (as above) after the catch, to close the streams in the case of an exception during write, but it complains that the close() method has an uncaught exception.[/quote]That's what you'd have to do.  Alternatively, declare this function as throwing IOException and catch it at a higher level. 

The correct answer is here is to actually get very mad at Sun and then drunk, FWIW.

> Putting a try catch in the finally clause doesn't sound right to me, can anyone give me any tipsIt's perfectly legal, just remember to structure things correctly so you cover all cases.

[quote=index_0@ya.com]thiink u can catch at function start block

public void myFunction throws Exception{
// do whatever u want !!!
}[/quote]No, that's not what that means.  Please go read a basic Java tutorial.

[quote=macxek]In that case, if you throw a generic Exception, the method that invokes the method you're working on won't be able to determine what went bad[/quote]That's not what that clause means either.  The method is free to throw anything that's a child of exception, which is why you generally never place Exception in a checked exceptions clause.

---

### Post by ruzle0 on 2006-04-27
Thanks a lot for the info guys, its better for me to get it right now than to try and fix misconceptions later when they're properly wedged in the noodle. and especially sphinx for showing a more concise solution too.

---

### Post by macxek on 2006-04-27
[QUOTE=LordHunter317]That's not what that clause means either.  The method is free to throw anything that's a child of exception, which is why you generally never place Exception in a checked exceptions clause.[/QUOTE]

You're absolutely right, my explanation was very badly worded.. Thanks for adding precision :) 

[QUOTE=sphinx]dammit macxek, you've snuck a comment in while I've written mine again! second day in a row![/QUOTE]

Haha, sorry, that's what usually happens with forums!

---

