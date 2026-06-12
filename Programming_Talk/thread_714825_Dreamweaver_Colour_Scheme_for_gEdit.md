---
title: "Dreamweaver Colour Scheme for gEdit??"
date: 2008-03-04
forum: Programming Talk
---

### Post by soapytheclown on 2008-03-04
Hi all not really a programming question, but i suppose this still fits here,

basically what i really want is for my php css xhtml javascript etc to have the same colour scheme as that of dreamweaver since that is what im used to and im finding thats its taking longer to debug problems since they're not so obvious to me, im sure this would also benefit other web coders who previously used dreamweaver, since googling for a theme has produced very few results i was planning on creating my own and sharing with everyone else, so i began by editing some of the default files // the ones id downloaded but cant work out correctly how to style specific elements, this page:


[http://blogs.gnome.org/pbor/2007/08/01/gedit-style-schemes/](http://blogs.gnome.org/pbor/2007/08/01/gedit-style-schemes/)

says that all i need to do is do each line as:-

[HTML] <style name="element" foreground="color" background="color"/>[/HTML]

but trying combinations of name="
html:select
xhtml:option
php:if
"
etc...

using colors defined 

still hasnt given me anything back can someone take a look or work out what might be needed.

thanks in advance guys =D

---

### Post by PaulFr on 2008-03-08
AFAICT,

1. The syntax detection is from the various *.lang files in **/usr/share/gtksourceview-2.0/language-specs**. This establishes a set of context ids. To find list of contexts defined in php.lang for example> grep 'context id' php.lang.
2. If you review php.lang, you will find that the PHP if statement is lumped together with a number of other keywords into a single context called 'keyword'.
3. Now if you go to the **/usr/share/gtksourceview-2.0/styles** directory, you will find a number of theme .xml files. Copy any one of them to make a new file, say myspec.xml, and then insert a statement like ```
<style name="php:keyword"               foreground="#FF0000" bold="true"/>
```Note the **keyword** in **php:keyword** here refers to the id of the context specified in php.lang.

4. Now start gedit, and in **Edit->Preferences**, Add.. and then select your **myspec.xml** file created in step 3 above. Now all your PHP keywords will be red.

If you want the **if** keyword to be colored differently from other keywords, you will need to edit the php.lang file to remove **if** from the 'keyword' context, and create its own context with an id (for example, let's say the new context id is 'if'), then you can use **php:if** in your **myspec.xml** file.

Hope this helps.

---

### Post by Fabiano Shark on 2008-05-05
I created a scheme color based on dreamweaver:

[http://fshark.com/files/dreamweaver.xml](http://fshark.com/files/dreamweaver.xml)

Just save and add this XML on gedit's scheme colors by clicking *Edit->Preferences* -> *font & colors* tab. ;)

--
Regards,
**Fabiano Shark**
[http://fShark.com](http://fShark.com)

---

