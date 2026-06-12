---
title: "Custom Code Highlighting for gedit - and your system"
date: 2008-03-27
forum: Programming Talk
---

### Post by firecrow8 on 2008-03-27
This is a technique to define a custom language definition for your system for use in gedit and possibly other ide's that inherit the system definition for the language

by creating a new language definition xml file in:
/usr/share/gtksourceview-2.0/language-specs/

or editing the existing files to fit your needs.
i.e. grouping functions into seperate categories to be colored differently than each other for better recognition while your programming.

you then create a xml file for the style in:
/usr/share/gtksourceview-2.0/styles/

and then select that style xml file in gedit.

previous versions of gedit had an interface for customizing the colors and future versions are expected to as well but currently editing the xml files is the only way to achieve these results.

to find out if you have the interface in your version of gedit. go to 
edit>preferences
if you see a tab called 'highlighting syntax' you have the interface. if not you don't and should follow what I've laid out below.

**the language xml file**
my suggustion is to copy an existing language file and then rename it. I copied php.lang because it's the language I'm most familiar with

I renamed it fc_comdoc.lang  and made a syntax for making my checklists pretty colors. and readable at a glance.

_major sections in the document and how they work_ 


a quick overview:
- language root tag, 
--- id attribute is used for identifying which context tags to load 
--- _name is what's displayed in the menu for syntax highlighting
--- _section is the section it is grouped under in the syntax highlighting menu

- styles tag
--- style tag defines the style
------ id attribute is what is referenced by the context tag
------ map-to attribute is used to redirect it to a different style

- definitions tag is where the actual regular expression patterns are defined
--- id attribute is used by the last context tag which has the same id as the language in order to load the pattern
--- style-ref tag references an above style by it's id
--- some other attributes related to processing the pattern such as end-at-line-end

- the last context tag which has the same id as the language contains and include tag whose children are also context tags and these link to all the context tags defined above.

again in detail:

root tag is <language [attributes]>
attributes of this tag:
 - _section is the section it will be under view>highlight syntax>'section_name' gedit menu
 - _name attribute is what will show up in the "view>highlight syntax>section_name>'language name'

the first child of the language tag is <metadata>
relevant child tags
- <property name="mimetypes">text/x-php; etc...</property> this relates to the filetype defined in the name of a mime.types file. i don't think defining this is mandatory
- <property name="glob">*.php;*.phtml</property> this controls what file types are automatically selected to highlight under this language as defined by thier file extension

the next node is <styles> containing a series child of tags that look like
<style id="style_id_name_here" _name="style_name" map-to="type:style_id">
- id : this is the id tag referenced by the style-ref attribute of the definition>context tags (see below)
- the _name tag I have no idea what this does. presumably gives it a name...
- the map-to tag redirects the style to another style. this tag is optional. the purpose is to be able to change one style in the style xml file which will change multiple styles, all that have a map-to attribute with a value pointing to them.

the next tag is <definitions> which has several <context> child tags
the context tags define the actual patters gedit will search for highlighting
<context [attributes]>
the context attributes are as follows
- id this is the id that will be referenced below in the last context tag whos id matches the id of the language (more on this below)
- style-ref  this references the id of one of the styles defined above in the <styles> tag(s)
- some other properties pertaining to treatment of the regular expression such as end-at-line-end and extend-parent

the child tags for the <context> tag include <start> , <end>, <include> and a few others. these are the tags that define the regular expression for pattern matching which i wont go into in detail.

the most important thing and the thing your most likely to overlook is this:
the last context tag must have the same id as the id of the language
and must reference all of the context tags above as new context tags with the attribute ref="id of above context tag"

only context tags referenced here will be loaded.



**the style xml file**
in:
/usr/share/gtksourceview-2.0/styles/

this file is much simpler on the condition that your aware of the namespace syntax.

the first tag is <style [options]>
the id and name attributes are used for reference in the preferences tab

the <color> tags
these define colors that can be referenced throughout this xml document

the <style> tags
these are the styles, the actual colors and font formatting that will be applied to the pattern matches.
attributes:
- name - this is how the style links to the tags in the languages. the namespace formatting is as follows  name="language:style" where language is the name of the language and style is the id of the style tag in the language xml file.
e.g. name="php:function" will refer to the style tag whose id=function in the php language document. 

that's it custom highlighting in gedit.

also the language files are probably used else where in the system as their not in the gedit folder so they make effect highlighting in other programs too which is good, or bad depending on what you want. 

post any questions you have. or point out anything in this that is vaugue or confusing. 

I'm sooooo excited to be able to customize the highlighting of languages and even make my own. I've created a new language txtcd for text comand document and txtap for text action plan and have been so happy with how much easier it is to keep track of my tasks when I can alter the colors to prioritize my list by adding a few charactors at the begining of the line for the task such as. 
->
+>
!+>
or
=

enjoy

and seriously post your questions (or criticisms). don't be shy.

---

### Post by joseloc on 2008-03-28
HI, I customizing a new language for rhtml files (Ruby embedded code) the sintax is <%= ...... %> i want to highlight the code in this block like textmate or netbeans, but I can't. yo now if it is posible make this?? I using gtksourceview 2.0 and gedit.

Thanks

---

### Post by firecrow8 on 2008-03-29
yeah it's absolutely possible. 

what exactly the regular expression would be i'm not sure of.

but my suggustion is to copy the language files you like and then rename them be rhtml and alter than to your liking. 

there may be an existing ruby definition file that you could download if you search for it. my example is for customizing a language basically from scratch. 

did you try what I laid out above? if so did it work?

---

### Post by joseloc on 2008-03-29
This is a post in my blog 

[http://blog.nationcode.com/articles/2008/03/21/gedit-como-textmate-para-gtksourceview-2-0](http://blog.nationcode.com/articles/2008/03/21/gedit-como-textmate-para-gtksourceview-2-0)

Is in spanish :)

but the sintax is for example <%= link_to "Hello", :action => "hello" %>

I want to set a background color to all code in this pattern <%= code in ruby %> to To highlight this code of other

Sorry if my English is bad :-)

---

### Post by firecrow8 on 2008-03-31
your english is good enough :)

take a look at the php.lang file 

it has a pattern defined for something similar <?php  blah blah ?> copy its structure and make it <%= alkjksldkjf %>

then find the value of the style-ref attribute

and what the style map-to attribute is

change that to something custom

then define it in the style file

<style name="newbgthingy"  background="#COLOR" />

---

### Post by neocortex on 2008-04-03
Hello!
I would appreciate any help very much, since I am now frustrated with the fact that I cannot make any progress in making new syntax highlight.
In very brief, I made Rnw.lang file for gtksourceview-1.0, to highlight a combination of R and LaTeX syntax. It worked very nice. But now, I cannot make the same for gtksourceview-2.0, althought I did more or less the same -- making new lang-file from latex.lang, with two major changes: (1) marking only dollar-sign ($) and not the character between, and (2) marking pieces of R-code that appears between <start>&lt;&lt;</start> and <end>@[\n ]+</end>. Here is my old gtksourceview-1.0 Rnw.lang file:
```

<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE language SYSTEM "language.dtd">
<language _name="Rnw" version="1.0" _section="Markup" mimetypes="text/x-Rnw">

	<escape-char>\</escape-char>

	<line-comment _name="Comment" style="Comment">
		<start-regex>%</start-regex>
		<start-regex>#</start-regex>
	</line-comment>

	<block-comment _name = "R Environment" style = "R code">
		<start-regex>&lt;&lt;</start-regex>
        	<end-regex>@[\n ]+</end-regex>
	</block-comment>

	<block-comment _name = "Comment Environment" style = "Comment">
		<start-regex>\\begin\{comment\}</start-regex>
        	<end-regex>\\end\{comment\}</end-regex>
	</block-comment>

	<keyword-list _name = "Include" style="Preprocessor" case-sensitive = "TRUE"
		match-empty-string-at-beginning = "FALSE"
		match-empty-string-at-end = "FALSE"
		beginning-regex = "\\">
		<keyword>input</keyword>
		<keyword>include</keyword>
		<keyword>includeonly</keyword>
		<keyword>usepackage</keyword>
		<keyword>$</keyword>
	</keyword-list>

	<keyword-list _name = "Command" style = "Keyword" case-sensitive = "TRUE"
		match-empty-string-at-beginning = "FALSE"
		match-empty-string-at-end = "FALSE"
		beginning-regex = "\\">
		<keyword>\\</keyword>
		<keyword>begin</keyword>
		<keyword>end</keyword>
		<keyword>documentclass</keyword>
		<keyword>newcommand</keyword>
		<keyword>newenvironment</keyword>
		<keyword>newtheorem</keyword>
		<keyword>newfont</keyword>
		<keyword>part</keyword>
		<keyword>chapter</keyword>
		<keyword>section</keyword>
		<keyword>subsection</keyword>
		<keyword>subsubsection</keyword>
		<keyword>paragraph</keyword>
		<keyword>subparagraph</keyword>
		<keyword>page</keyword>
		<keyword>equation</keyword>
		<keyword>figure</keyword>
		<keyword>table</keyword>
		<keyword>footnote</keyword>
		<keyword>footnotemark</keyword>
		<keyword>footnotetext</keyword>
		<keyword>mpfootnote</keyword>
		<keyword>enumi</keyword>
		<keyword>enumii</keyword>
		<keyword>enumiii</keyword>
		<keyword>enumiv</keyword>
		<keyword>label</keyword>
		<keyword>pageref</keyword>
		<keyword>ref</keyword>
		<keyword>onecolumn</keyword>
		<keyword>twocolumn</keyword>
	</keyword-list>

	<keyword-list _name = "Math" style="Math" case-sensitive = "FALSE"
		match-empty-string-at-beginning = "FALSE"
		match-empty-string-at-end = "FALSE"
		beginning-regex = "">
		<keyword>\$</keyword>
	</keyword-list>

	<pattern-item _name = "Keyword" style = "Others">
		<regex>\\[a-zA-Z]+</regex>
	</pattern-item>

</language>

```
Can anyone help me to make this changes in new gtksourceview-2.0. I thought I did everything right, but there is no highlight at all.

Best,
PM

---

### Post by the_darkside_986 on 2008-04-14
I'm having the same trouble trying to add MiniD highlighting. Not a single word is highlighted after I copied straight from another file and changed the id values. Perhaps all the syntax highlighting is hard-coded and all those lang files are just to mess with our heads? It would be a miracle to add syntax highlighting without needing the source tree and trying to recompile.

---

### Post by derlinus on 2008-04-24
I would like to highlight the content of latex footnotes. Therefore, I modified the content of the latex.lang file accoring to [http://forum.ubuntuusers.de/topic/163933/?p=1325568#1325568](http://forum.ubuntuusers.de/topic/163933/?p=1325568#1325568) :

I deleted the following code in line 69:

```
<keyword>footnote</keyword>
```
. After the list of "common-commands" I added 


```
<context id="footnote" style-ref="footnote">
<start>\\footnote\{</start>
<end>}</end>
</context>
```
. At the top of the file, I added the following to the styles-section:

```

<style id="footnote"           _name="Footnote"   map-to="def:function"/>
```
. At least, I added the following to the <context id="latex"> list 

```
<context ref="footnote"/>
```
. The complete modified latex.lang file can be found here: [http://ubuntuusers.de/paste/153193/]("http://ubuntuusers.de/paste/153193/") 
.

Now, the footnote content is highlighted, but there is one problem left: The highlighting ends with the first bracket. For example, 

```
\footnote{This is a \cite[1]{test} entry}
```
doesn't highlight the word "entry" any more.

Is there any chance to solve this problem? I would be very glad! :)

Thanks, Jan

---

### Post by neocortex on 2008-04-28
This is nice! But, you modified existing *.lang file. The question is how to introduce new one.

Best,
PM

---

### Post by escentrix on 2008-11-19
Lately gedit has been giving me a headache. I am trying to add a few keywords to the php lang file, more specifically mysql functions. I would really like them to be a different color so that I can easily tell them apart from the rest of my code.

Here's what I have so far:

_*In my php.lang file (/usr/share/gtksourceview-2.0/language-specs/php.lang)*_
```

<?xml version="1.0" encoding="UTF-8"?>

<language id="php" _name="PHP" version="2.0" _section="Scripts"
...
...
  <styles>
    ...
    ...
    <style id="mysql" _name="Mysql Functions"/>
  </styles>

  <definitions>
    ...
    ...

    <context id="mysql" style-ref="mysql">
       <keyword>mysql_fetch_array</keyword>
       <keyword>mysql_query</keyword>
       <keyword>mysql_connect</keyword>
       <keyword>mysql_select_db</keyword>
       <keyword>mysql_error</keyword>
    </context>

    ...
    ...
  </definitions>
</language>

```

_*In my custom.xml file (/usr/share/gtksourceview-2.0/styles/custom.xml)*_
```

<?xml version="1.0" encoding="UTF-8"?>

<style-scheme id="custom" _name="Custom" version="1.0">
  ...
  ...
  <style name="php:mysql"                   foreground="#A822D8" bold="true"/>
  ...
  ...
</style-scheme>

```

Am I using my id's wrong or should this work? Right now none of my mysql keywords are being styled they are black normal text. And for the record, I am using my 'Custom' color scheme in gedit.
When I change other color values it does modify it in on my code. For instance if I change the style of statements in custom.xml they do in turn change in gedit, so I know that some things are actually working (just not mine)!

---

### Post by escentrix on 2008-11-19
After staring at the lang file for the last 2 hours something caught my attention.
I noticed that my php-block context list was organized very suspiciously...

```
    <context id="php-block">
      <start>&lt;([?](php)?)</start>
      <end>[?]&gt;</end>
      <include>
        <context sub-pattern="0" where="start" style-ref="keyword"/>
        <context sub-pattern="0" where="end" style-ref="keyword"/>
        <context ref="cpp-line-comment"/>
        <context ref="bash-line-comment"/>
        <context ref="c-block-comment"/>
        <context ref="double-quoted-string"/>
        <context ref="single-quoted-string"/>
        <context ref="backtick-string"/>
        <context ref="here-doc-string"/>
        <context ref="variable"/>
        <context ref="array-operators"/>
        <context ref="mysql"/>
        <context ref="keywords"/>
        <context ref="operators"/>
        <context ref="type"/>
        <context ref="null-value"/>
        <context ref="boolean"/>
        <context ref="float"/>
        <context ref="decimal-number"/>
        <context ref="octal-number"/>
        <context ref="hexadecimal-number"/>
	<context ref="identifier"/>
      </include>
    </context>
```

I originally had **<context ref="mysql"/>** just amended to the end. I noticed though that everything is listed in order as it appears down the file. When I moved the context to the correct order as it is listed everything worked. Seems odd, but everything is working now so I'm not really concerned anymore!

Maybe this can help with some of the other problems you guys were having, that is if you are still looking...

---

### Post by TwoD on 2009-12-30
Something useful worth noting is that any of these files when put in **~/.gnome2/gtksourceview-1.0/[language-specs | styles]** will override those in **/usr/share/gtksourceview-2.0/[language-specs | styles]** so all users can have their own preferences. It also makes backups of modifications a lot easier on single-user systems as well.

I tried using /usr/share/gtksourceview-2.0, as it was present on my install and the gedit package depends on it, but when using the below technique files were only picked up by gedit from the 1.0 folder.

(On a general note, many other programs use this way of overriding default system settings in /usr/share or maybe /etc.)

---

### Post by romunov on 2010-01-07
Hi,

I'm running Oblivion theme in gedit and am trying to customize the R syntax, to make it a bit more structured and contrasting. I run Ubuntu Karmic (9.10).

I have created directories "styles" and "language-specs" in /.gnome2/gtksourceview-2.0/ which contain oblivion.xml and R.lang, respectively. These are the default files from /usr/share/gtksourceview-2.0/. So far, I have tried editing the oblivion.xml, but I must be doing something wrong, because I don't see any changes in the syntax highlighting.

I have added new color (skyblue4) and these lines at the bottom:
```
  <!-- R language -->
  <style name="r:reserved-classes"		foreground="skyblue4"/>
```
This should color the reserved-classes as defined in the R.lang:
```
<context id="reserved-classes" style-ref="reserved-classes">
      <keyword>array</keyword>
      <keyword>character</keyword>
      <keyword>complex</keyword>
      <keyword>data.frame</keyword>
      <keyword>double</keyword>
      <keyword>factor</keyword>
      <keyword>function</keyword>
      <keyword>integer</keyword>
      <keyword>list</keyword>
      <keyword>logical</keyword>
      <keyword>matrix</keyword>
      <keyword>numeric</keyword>
      <keyword>vector</keyword>
    </context>

```

Can someone point me to the (obvious?) problem? Am I missing something?

---

### Post by CHW on 2010-01-25
Hello,

Is it also possible to import this custom code highlighting into KDE applications like Kile or Kate under Gnome?

I use Ubuntu 9.10.

Regards,
CHW

Edit: It doesn't seem so, they use a different file format.
Never mind, I'll stay with Gedit, it also has some nice plugins which fit my needs.

---

### Post by onykage on 2010-10-05
Can anyone tell me why when i add a new *.lang file that the highlighting acts like plain text?  By plain text i mean that all highlighting completely goes away and all thats left is plain text.

is there something that is missing or left to be changed?

in regression what i did was rename the c-sharp.lang to new.lang, changed the c-sharp keywords to my custom list of keywords and changed all occurrences of "c-sharp" to "new".  I can see the language in the list but when its activated, again the text loses all highlighting and returns to plain text.

thanks in advance for any help.

---

