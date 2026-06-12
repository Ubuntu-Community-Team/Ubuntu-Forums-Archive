---
title: "Tip to improve gedit syntax highlight"
date: 2007-01-14
forum: Outdated Tutorials &amp; Tips
---

### Post by ayoli on 2007-01-14
i really like gedit and find it very powerful with plugins, but i was missing something in syntax highlight for php:correct highlight for heredoc strings like:
```
echo <<<HTML
   <p> big string bloc with non interpreted " or ' </p>
HTML;
```
i've just edited the xml language file for php located in /usr/share/gtksourceview-1.0/language-specs/php.lang where i add this:
```
	<!-- 'heredoc strings' -->
	<string _name = "Heredoc String" style = "String" end-at-line-end = "FALSE">
		<start-regex>&lt;&lt;&lt;</start-regex>
		<end-regex>[A-Z]+[;]$</end-regex>
	</string>
```

edit: added a $ to specify that we are at end of line.

hope the tip will help :)

---

