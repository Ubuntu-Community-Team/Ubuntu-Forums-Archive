---
title: "gedit snippets"
date: 2007-09-27
forum: Programming Talk
---

### Post by nduplessis on 2007-09-27
Hey guys

I just installed Ubuntu, loving it!
I am doing PHP/XHTML programming and quite like gedit. I am coming from a Mac background, programming in Textmate which is awesome.

The question I have is about gedit and snippets. Are snippets linked to certain files? I.e. do HTML snippets work in .php files? I can't seem to get the HTML snippets to work in a PHP file

Regards,

---

### Post by mario.kostelac on 2007-09-27
Yes, snippets are linked to certain file... If you have PHP file, you may use php snippets, if you use html, you may use html snippets... Maybe there is some trick for doing what you want..
If you will ever know post this here please...

---

### Post by nduplessis on 2007-09-27
Ye, it only makes sense to mix PHP and HTML since they are often mixed

---

### Post by kane77 on 2007-10-03
> **nduplessis said:**
> Hey guys

I just installed Ubuntu, loving it!
I am doing PHP/XHTML programming and quite like gedit. I am coming from a Mac background, programming in Textmate which is awesome.

The question I have is about gedit and snippets. Are snippets linked to certain files? I.e. do HTML snippets work in .php files? I can't seem to get the HTML snippets to work in a PHP file

Regards,

the snippets work by looking at what your highlight mode is if it is php it offers you php snippets if it is html highlight mode it gives you html...
you might use the quick highlight mode plugin or you can copy the html snippets to php snippet file.
(the file is located in /usr/share/gedit-2/plugins/snippets/) they are an xml files that have form:
```
<snippet>
<text>*Here goes the text of the snippet*</text>
<tag>tag_here</tag>
<description>a name for your snippet..</description>
</snippet>

```

I guess as long as you have non-coliding tags you can just copy (append) content of html.xml to php.xml (or vice versa) and mix them up as you like..

---

### Post by rudasn on 2008-06-02
Is there a way to change the key binding from Tab to something else? I am using the Word Completion plugin ([http://users.tkk.fi/~otsaloma/gedit](http://users.tkk.fi/~otsaloma/gedit)) that also uses Tab key to insert words and so it prevents Snippets from working properly.

Edit: To rephrase: is there a way to use both Snippets and Word Completion without those two intereffering with each other?

Cheers

---

### Post by nimxor on 2009-01-24
if you go here

```
/usr/share/gedit-2/plugins/snippets
```

You will see many .xml files which are where snippets are saved.
For merging html and php snippets there are two ways

**--- 1**

Just open html.xml file and copy all the snippets in the php.xml one.

Pay attention:
1. you need root privileges for editing php.xml
```
cd /usr/share/gedit-2/plugins/snippets/
gksudo gedit php.xml
```
2.just copy nodes marked as <snippet> such as this
```
  <snippet id="doctype">
    <text><![CDATA[<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN"
	"http://www.w3.org/TR/html4/strict.dtd">
]]></text>
    <description>HTML &#8212; 4.01 Strict</description>
    <tag>doctype</tag>
  </snippet>
```
do not copy the root tag <snippets language="HTML"> and its closing counterpart </snippets> at the end of the file


**--- 2**

1. make a copy of the original html.xml file and rename it i.e. html-for-php.xml
2. in the copy change the attribute in the root snippets tag so this 
```
<snippets language="HTML">
```
becomes 
```
<snippets language="PHP">
```
if you restart gedit it will read both php.xml and html-for-php.xml files as snippet repositories for .php files




--- UPDATE
Sorry, I came here after a Google search which brought me to an Archive page for this topic and I am new t this forum, so I didn't see that Kane77 had already answered the question.

---

### Post by Rob Edwards on 2010-06-22
Old thread, new note.

Had the same problem - Always wanting to switch between server side, JS, HTML, CSS.

I use this [http://empty.23inch.de/pmwiki.php/Main/EditShortcuts](http://empty.23inch.de/pmwiki.php/Main/EditShortcuts) to bind the language to a shortcut key e.g. I use ctrl+alt+j for Javascript, ctrl+alt+h for html.

Works well.

---

### Post by Andrew_P on 2011-09-02
> **nduplessis said:**
> The question I have is about gedit and snippets. Are snippets linked to certain files? I.e. do HTML snippets work in .php files? I can't seem to get the HTML snippets to work in a PHP file.

Define the snippets you want to use everywhere as "Global" so you can use them in whatever file mode you're using gedit.  The Global section should appear at the top of the list in the left pane of the Snippets Manager.  For example, I've defined a snippet called "Lorem ipsum copyblock" that injects the following Latin text:

[FONT="Fixedsys"]Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.[/FONT]

To use it, I type the Tab trigger ```
Lorem<Tab>
``` and gedit squirts it into the file. It's useful in a number of situations when I need to quickly generate a block of gibberish text for testing purposes.;)

---

