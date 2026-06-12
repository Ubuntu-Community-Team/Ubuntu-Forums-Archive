---
title: "gedit syntax highlighting - adding a new type"
date: 2008-11-01
forum: Programming Talk
---

### Post by wmsedgar on 2008-11-01
Hi,

I'm a recent linux convert running Ubuntu 8.04 with gnome and trying to create a new syntax highlighting file for gedit.  I'm doing some work with MIPS assembler; enough that highlighting would be useful. I've seen similar in vim, but would prefer to use gedit.  I've read various posts, which led me to create a mips.lang definition file (attached) and drop it into */usr/share/gtksourceview-2.0/language-specs*.  I created it based on content from other language spec files I found there.  I also created a mips.xml file and dropped it into */usr/share/mime/packages* and then ran *update-mime-database*.

I've seen in other posts that an x-asm.xml file may be required in */usr/share/mime/text*, but I've no idea how to create that file, or if it's really necessary.

Based on the changes I've made gedit does recognize the *.asm files when I open them, but does not do any highlighting for some reason.  I'm guessing that either my language definition file is somehow flawed, or that I'm missing some crucial step. Any suggestions or help would be greatly appreciated.

-Bill

---

### Post by ericwait on 2009-03-08
I have been doing some programing for class using SAL (simple abstract language), which I think is what you are looking for.  I have been using gedit to do so.  Here is my lang file that does some simple coloring for me.

Copy the code below into a file named:
```
/usr/share/gtksourceview-2.0/language-specs/sal.lang
```
or rename the attched doc (remove the .txt) and place it there.

This is the path for Ubuntu 8.10, I also noticed there was a gtksourceview-1.0, but placing it in there had no effect.

```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE language SYSTEM "language.dtd">
<!--Created using the CPP.lang file as a template-->
<language _name="SAL" version="1.0" _section="Sources" 
           mimetypes="text/x-c++src;text/x-c++hdr">
	
	<escape-char>\</escape-char>

	<line-comment _name = "Line Comment" style= "Comment">
		<start-regex>#</start-regex>
	</line-comment>


	<block-comment _name = "'#if 0' Comment" style = "Comment">
		<start-regex>^[ \t]*#[ \t]*if[ \t]*0</start-regex>
        	<end-regex>[ \t]*#[ \t]*(endif|else)</end-regex>
	</block-comment>

	<string _name = "String" style = "String" end-at-line-end = "TRUE">
		<start-regex>&quot;</start-regex>
		<end-regex>&quot;</end-regex>
	</string>


	<keyword-list _name = "Keywords" style = "Keyword" case-sensitive="TRUE">
		<keyword>move</keyword>
		<keyword>add</keyword>
		<keyword>sub</keyword>
		<keyword>mul</keyword>
		<keyword>div</keyword>
		<keyword>rem</keyword>
		<keyword>cvt</keyword>
		<keyword>not</keyword>
		<keyword>and</keyword>
		<keyword>or</keyword>
		<keyword>nand</keyword>
		<keyword>nor</keyword>
		<keyword>xor</keyword>
		<keyword>sll</keyword>
		<keyword>srl</keyword>
		<keyword>sra</keyword>
		<keyword>rol</keyword>
		<keyword>ror</keyword>
		<keyword>b</keyword>
		<keyword>j</keyword>
		<keyword>beq</keyword>
		<keyword>bne</keyword>
		<keyword>blt</keyword>
		<keyword>bgt</keyword>
		<keyword>ble</keyword>
		<keyword>bge</keyword>
		<keyword>beqz</keyword>
		<keyword>bnez</keyword>
		<keyword>bltz</keyword>
		<keyword>bgtz</keyword>
		<keyword>blez</keyword>
		<keyword>bgez</keyword>
		<keyword>la</keyword>
		<keyword>put</keyword>
		<keyword>get</keyword>
		<keyword>puts</keyword>
		<keyword>getc</keyword>
		<keyword>putc</keyword>
		<keyword>nop</keyword>
	</keyword-list>

	<keyword-list _name = "Types" style = "Data Type" case-sensitive="TRUE">
		<keyword>data</keyword>
		<keyword>text</keyword>
		<keyword>word</keyword>
		<keyword>byte</keyword>
		<keyword>float</keyword>
		<keyword>space</keyword>
		<keyword>asciiz</keyword>
		<keyword>ascii</keyword>
	</keyword-list>

	<string _name = "Character Constant" style = "String" end-at-line-end = "TRUE">
		<start-regex>&apos;</start-regex>
		<end-regex>&apos;</end-regex>
	</string>

	<pattern-item _name = "Decimal" style = "Decimal">
		<regex>\b([1-9][0-9]*|0)([Uu]([Ll]|LL|ll)?|([Ll]|LL|ll)[Uu]?)?\b</regex>
	</pattern-item>

	<pattern-item _name = "Floating Point Number" style = "Floating Point">
		<regex>\b([0-9]+[Ee][-]?[0-9]+|([0-9]*\.[0-9]+|[0-9]+\.)([Ee][-]?[0-9]+)?)[fFlL]?</regex>
	</pattern-item>

	<pattern-item _name = "Octal Number" style = "Base-N Integer">
		<regex>\b0[0-7]+([Uu]([Ll]|LL|ll)?|([Ll]|LL|ll)[Uu]?)?\b</regex>
	</pattern-item>

	<pattern-item _name = "Hex Number" style = "Base-N Integer">
		<regex>\b0[xX][0-9a-fA-F]+([Uu]([Ll]|LL|ll)?|([Ll]|LL|ll)[Uu]?)?\b</regex>
	</pattern-item>


</language>
```

I hope this helps. Please post your file if you have any improvements.:-D

---

### Post by ericwait on 2009-05-06
I have also made files for MAL and TAL.  I am sure this is only useful for students that are programing in these languages, but here you go.

---

### Post by uKev on 2009-06-18
Hi,

any news on this? I need MIPS assembler syntax highlighting, too. It would be great, if it would work with gedit.

Thanks a lot for any response.

---

### Post by rCXer on 2009-06-18
I know that the [KATE](http://en.wikipedia.org/wiki/Kate_(text_editor)) text editor has highlighting for MIPS.  Just install it through package manager.  On KATE's menu just goto Tools-> Higlighting -> Assembler-> MIPS Assembler.

---

### Post by ericwait on 2009-06-18
You can use the code above for the MIPS. Just pick which format (most likly SAL) that you will be coding with.  If there is something missing, let me know.

---

### Post by ulgor on 2010-06-10
I tried to write my custom syntax highlighting file for Gedit as well, and have the same problem: 
- Since the target syntax is similar to VB, I duplicated the vbnet.lang in /usr/share/gtksourceview-2.0/language-specs and renamed itgl
- I changed the id, name, category(scripts), file-extension but not the mimetype
- I removed/added some keywords, no major changes to the XML structure itself...

Under View>Highlight>Scripts my custom syntax definition shows up, but when I choose it, no styles are applied! How can I make sure the styles are used? I am curious, because even though I made an exact copy of the VB-definition, just changing id and file extension, gedit stops applying any style to my code...

---

