---
title: "xGettext and Gettext"
date: 2007-06-30
forum: Programming Talk
---

### Post by v8YKxgHe on 2007-06-30
Hey, 

I'm (finally) adding language support to my open-source PHP CMS and after much thinking I've decided to go with Gettext for translations/locale. I've got it working great, however I have to create the Pot manually!

The way I am doing Gettext is different to your normal:

```

echo _( 'Hello over there!' );
// Or
echo gettext( 'Hello over there!' );

```

Instead, as I using a custom-built MVC Framework - in my View files I have tags like the following:

```
<p>{L_[Hello over there!]}</p>
```

Then in my view class it simply uses reg-ex to get every language 'tag' - here is the code if you're interested:

```

		//---
		// language_tags() provides the Zula framework with language support for
		// views. It finds all tags that are in the format of {L_[phrase]} and replaces
		// then with the correct translation
		// @param string $content
		// @return string
		//---
		private function language_tags( $content ) {
			Registry::get( 'locale' )->update_text_domain( 'messages', Zula::get_dir( 'controllers' ).'/'.$this->module.'/locale' ); 
			preg_match_all('@{L_\[(.[^\]]*)]}@', $content, $tags);
			#Zula::debug_print( $tags );
			if ( !empty( $tags[0] ) ) {							
				foreach( $tags[0] as $key=>$tag ) {
					$tag = trim( $tag, '{} ' );
					$value = gettext( $tags[1][ $key ] );
					$this->assign( array( $tag => $value ), false );
				}
			}
		}

```

As my View files also allow for PHP code, I do in _some_ of them have:

```
<?php echo gettext( 'Hello over there!' ); ?>
```

Now, I have to create the pot files manually because xgettext only looks for _() or gettext() for it to generate the pot files from, and this just wont work with how I am doing it. 

I am wondering if there is a way to ... change how xgettext searches for the strings it needs, so I don't have to do the very painful process of creating my pot files manually!

Thanks!

---

### Post by mihai.ile on 2009-04-22
there is a way, I use:

```

xgettext -n *.php --keyword=msg

```

where "msg" is my custom method that I use in php files for sending strings, for example:

```

print msg('My favorite foods are').":\n";
print msg('french fries')."\n";

```

after the "xgettext" call I end up with a .po file that contains:

```

#: index.php:41
msgid "My favorite foods are"
msgstr ""

#: index.php:42
msgid "french fries"
msgstr ""

```


EDIT: i know thread is old, probably not much use for the thread starter but I had the same problem and could be useful for others...

---

