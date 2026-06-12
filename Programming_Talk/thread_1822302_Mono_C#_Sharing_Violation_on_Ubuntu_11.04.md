---
title: "Mono C# Sharing Violation on Ubuntu 11.04"
date: 2011-08-10
forum: Programming Talk
---

### Post by jambel on 2011-08-10
Hello, 

I had developed an application and so far in Ubuntu 10.10 worked fine. I'm trying to run it under 11.04 and I get that error: 

Unhandled Exception: System.IO.IOException: Sharing violation on path /home/will/[Unknown] 
  at System.IO.FileStream.ReadData (IntPtr handle, System.Byte[]  buf, Int32 offset, Int32 count) [0x00000] in <filename unknown>:0  
  at System.IO.FileStream.ReadInternal (System.Byte[] dest, Int32 offset, Int32 count) [0x00000] in <filename unknown>:0  
  at System.IO.FileStream.Read (System.Byte[] array, Int32 offset, Int32 count) [0x00000] in <filename unknown>:0  
  at System.IO.StreamReader.ReadBuffer () [0x00000] in <filename unknown>:0  
  at System.IO.StreamReader.Read () [0x00000] in <filename unknown>:0  
  at System.TermInfoDriver.ReadKeyInternal (System.Boolean& fresh) [0x00000] in <filename unknown>:0  
  at System.TermInfoDriver.ReadLine () [0x00000] in <filename unknown>:0  
  at System.ConsoleDriver.ReadLine () [0x00000] in <filename unknown>:0  
  at System.Console.ReadLine () [0x00000] in <filename unknown>:0  
  at jaNET.MainClass.Main (System.String[] args) [0x00000] in <filename unknown>:0  

I run the program step by step and I determine that the error comes at Console.ReadLine() 

Here is the main code: 

while(Parser.ParserState) 

{ 
Console.Write(Methods.whoami() + ">"); 
Console.ForegroundColor = ConsoleColor.Green; 
string cmdReader = Console.ReadLine(); <-- it crashes here when first command completed 
Console.ResetColor(); 
if (cmdReader.Length > 0) 
Parser.Parse(cmdReader, true, true); 
} 

Any ideas? 

Thanks in advance!

---

### Post by jambel on 2011-10-06
anyone? :(

---

### Post by karlson on 2011-10-06
> **jambel said:**
> 
Here is the main code: 

while(Parser.ParserState) 

{ 
Console.Write(Methods.whoami() + ">"); 
Console.ForegroundColor = ConsoleColor.Green; 
string cmdReader = Console.ReadLine(); <-- it crashes here when first command completed 
Console.ResetColor(); 
if (cmdReader.Length > 0) 
Parser.Parse(cmdReader, true, true); 
} 

Any ideas? 

Thanks in advance!

My C# is a bit rusty but aren't you supposed to do:
```

string reader = new string;

```
before you use it?

---

### Post by jambel on 2011-10-06
> **karlson said:**
> My C# is a bit rusty but aren't you supposed to do:
```

string reader = new string;

```before you use it?

No, it works fine in ubuntu 10.10

Thanks for your answer

---

