---
title: "I need a wysiwyg editor that can wrap programming code an display it accordingly"
date: 2007-01-02
forum: Programming Talk
---

### Post by manilodisan on 2007-01-02
I need a wysiwyg editor that can wrap programming code an display it accordingly like this one from vBulletin. I have a huge issue with this when I write programming articles. Or someone who knows how to integrate it. Any ideas please.

---

### Post by Mirrorball on 2007-01-02
Just wrap your code in <pre> HTML tags. Then the browser won't wrap lines or mess the whitespace. This is what the WYSIWYG editor does, it wraps the code in <pre> tags.

---

### Post by manilodisan on 2007-01-02
I need something that takes the code and does things like this (te reader will see the code highlighted - I've selected the code and pressed "php" to let the editor know that this is PHP code so it will display colors and stuff):

[PHP]<?php
function keywords_createRewriteRules($rewrite) {
	global $wp_rewrite;
	
	// add rewrite tokens
	$keytag_token = '%tag%';
	$wp_rewrite->add_rewrite_tag($keytag_token, '(.+)', 'tag=');
	
	$keywords_structure = $wp_rewrite->root . "tag/$keytag_token";
	$keywords_rewrite = $wp_rewrite->generate_rewrite_rules($keywords_structure);
	
	return ( $rewrite + $keywords_rewrite );
}

echo keywords_createRewriteRules("http://www.roscripts.com/catlistings.php?Id=22");
?>[/PHP]

etc.

---

### Post by Mirrorball on 2007-01-02
Oh. OK, it's not vB's WYSIWYG editor that does this. It's done on the server side with PHP's syntax highlighting functions. I'm not aware of any WYSIWYG editor that does this, sorry.

---

### Post by Houman on 2007-01-02
Hi there,

I dont know of a wysiwyg editor. But when I have to write reports with code in them I use latex. I write my article in whatever and then use one of several latex packages that read code and produce latex files which contain the properly formatted code ready to be compiled into a latex article.

You can check them out, the one in the repositories is: texify. 
But you have to append the right extension to it, so texify has options for many languages, I use texifyc++ for my C++ code. I dont think it provides syntax highlighting for C++. But it does proper indentation and the rest. There are similar packages to texify you can check out.


regards

Houman

---

