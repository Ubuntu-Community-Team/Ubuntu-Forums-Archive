---
title: "Execute Shell command in Mono"
date: 2006-12-17
forum: Programming Talk
---

### Post by hadiriazi on 2006-12-17
Hi all

I want to execute this command in mono using c# and get the results to show in a combobox.
How do I execute the command and get the results as a string or an array?
```

 sudo fdisk -l | grep NTFS
```

---

### Post by hadiriazi on 2006-12-17
Ok guys I now know how to execute the command, but how do I get the results?

I used this code to execute the command:

```

System.Diagnostics.Process proc = new System.Diagnostics.Process();
proc.EnableRaisingEvents=false; 
proc.StartInfo.FileName = "fdisk";
proc.StartInfo.Arguments = "-l | grep NTFS";
proc.Start();
proc.WaitForExit();
```

plz help me :(

---

### Post by rmjb on 2007-06-23
I have no idea if you still need this info, but your post was the first that came up when I searched in google for how to call a command from c#.

On this page there is some code that deals with reading the stdout & stderr:
[http://msdn2.microsoft.com/en-us/library/system.diagnostics.process(vs.80).aspx](http://msdn2.microsoft.com/en-us/library/system.diagnostics.process(vs.80).aspx)

HTH,
- rmjb

---

### Post by PandaGoat on 2007-06-24
He is correct.  Each process has a stream of data going in and out essentially.  System.Diagnostics.Process.StandardOutput is the stream of the output of the process.
[http://www.go-mono.com/docs/index.aspx?link=N%3ASystem.Diagnostics](http://www.go-mono.com/docs/index.aspx?link=N%3ASystem.Diagnostics)

It's gets a System.IO.StreamReader.  The member string ReadToEnd() will read all the data returned.  It is a synchronous call so you do not have to handle waiting until it returns anything.  It will block untill something is read.

Here is an example:
```

string data = process.StandardOutput.ReadToEnd();

Console.Writeline( data + " was returned" );

```

---

