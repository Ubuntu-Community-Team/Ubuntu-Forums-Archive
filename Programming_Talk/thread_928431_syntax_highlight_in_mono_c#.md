---
title: "syntax highlight in mono c# ?"
date: 2008-09-24
forum: Programming Talk
---

### Post by heikaman on 2008-09-24
Hello

I am trying to make a simple syntax highlighter in C# mono using a Windows.Forms.RichTextBox control from winforms after googling for a while I found a reasonable solution using the RTF so I tried it in my RichTextBox subclass

[PHP]
Rtf="{\\rtf1\\ansi\\ansicpg1252\\deff-1\\deflang1033"+
			"{\\fonttbl{\\f0\\fnil\\fcharset0 Nimbus Mono L;}}"+
			"{\\colortbl \\red0\\green0\\blue0;\\red255\\green0\\blue0;}"+
			"{\\*\\generator Mono RichTextBox;}";
[/PHP]

and then I got 

[PHP]

Unhandled Exception: System.NotSupportedException: CodePage 1252 not supported
  at System.Text.Encoding.GetEncoding (Int32 codePage) [0x00000] 
  at System.Windows.Forms.RTF.RTF.GetToken () [0x00000] 
  at System.Windows.Forms.RTF.RTF.ReadFontTbl (System.Windows.Forms.RTF.RTF rtf) [0x00000] 
  at System.Windows.Forms.RTF.RTF.RouteToken () [0x00000] 
  at System.Windows.Forms.RTF.RTF.Read () [0x00000] 
  at System.Windows.Forms.RichTextBox.InsertRTFFromStream (System.IO.Stream data, Int32 cursor_x, Int32 cursor_y, System.Int32& to_x, System.Int32& to_y, System.Int32& chars) [0x00000] 
  at System.Windows.Forms.RichTextBox.InsertRTFFromStream (System.IO.Stream data, Int32 cursor_x, Int32 cursor_y) [0x00000] 
  at System.Windows.Forms.RichTextBox.set_Rtf (System.String value) [0x00000] 
[/PHP]

Now I am really NOT a C# developer (I HAVE to do it in C#) and I don't know what was that all about :confused:

So any help is really appreciated, and I am open to suggestions if you know a better way to do this.

Thanks. :popcorn:

---

### Post by Zugzwang on 2008-09-24
> **heikaman said:**
> 
Unhandled Exception: System.NotSupportedException: CodePage 1252 not supported
[/PHP]


Dear OP (original poster),

[LIST]
[*] Whenever you get an error message like this, use google (or your other favorite search machine) to find for similar problems and its solutions. This is generally considered to be polite as it avoids answering the same question over and over again. In this case, you could have simply googled for: [.........."System.NotSupportedException: CodePage 1252 not supported"............], which would have yielded [.......[http://ubuntuforums.org/showthread.php?t=831409.........]](http://ubuntuforums.org/showthread.php?t=831409.........]). If you have already searched for the problem, please state here why the answers you found are insufficient. Also make sure to strip everything from the error message that it special for your case, like for example the class name of your class in which the error occured, your home path, etc.
[/LIST]

---

### Post by heikaman on 2008-09-24
Thanks :)

You're right I didn't search for the error :oops: but I also wanted to get other suggestions/ideas about syntax highlighting so I thought I post it anyway.

However, I still can't change the RTF for some reason when I:
[PHP]
Rtf="{\\rtf1\\ansi\\ansicpg1252\\deff-1\\deflang1033"+
			"{\\fonttbl{\\f0\\fnil\\fcharset0 Nimbus Mono L;}}"+
			"{\\colortbl \\red0\\green0\\blue0;\\red255\\green0\\blue0;}"+
			"{\\*\\generator Mono RichTextBox;}";
			
			Console.WriteLine(Rtf);
[/PHP]

I still get the default RTF:
[PHP]
{\rtf1\ansi\ansicpg1252\deff0\deflang1033
{\fonttbl{\f0\fnil\fcharset0 DejaVu Sans;}}
{\*\generator Mono RichTextBox;}\pard\f0\fs16 \par
}
[/PHP]

Any idea ? 

PS:
The error doesn't have my home path or the class name (I think unless I am missing it !)

---

