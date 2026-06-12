---
title: "Web page internationalisation methods"
date: 2013-12-17
forum: Programming Talk
---

### Post by theDaveTheRave on 2013-12-17
Hi all,

I'm looking for other peoples experiences in creating 'interntionalised' web pages -  ie multi-lingual.

Personally I can think of a number of different approaches to the problem, each propose advantages / disadvantages compared to the others. Here I wish to start a discussion to help us site developers choose the most appropriate tools and configuration for their site.

So here are the various options.
[U]
Inline definition using lang attribute[/U]

This seems like a reasonable solution on first investigation, but it quickly falls down as difficult to manage, this is my (likely naive) evaluation.

Easy to add a lang attribute to any element in your page, then turn these element of / off with a little bit of DOM manipulation, and JQuery. For instance....
```

<p lang = "en-uk" display = "true">a paragraph in english</p>

<p lang = "fr" display = "false">Quelque chose ecrit en francais</p>

```
Then using a cookie and a bit of JQuery you convert this too...
```

<p lang = "en-uk" display = "false">a paragraph in english</p>

<p lang = "fr" display = "true">Quelque chose ecrit en francais</p>

```
and hey presto... you get the language displayed that you would desire.

This seems like a reasonable solution, particularly for menu items, that will generally be short text, but once you get to larger sections you start need to do lots of editing.
Add to the problem that the page will load to the browser with all the languages available, not a big issue... but what if you have large sections with a lot of translations.... you will end up loading a very large page!
So my evaluation is that this is a 'naive' solution, although it may be sufficient in the first instance I can see it rapidly getting out of hand and being hard to manage, also you'll end up with a sort of page that is a complete 'tag soup'.

[U]
Include external pages into current page[/U]

This solution has some of the problems of the above approach, but now we have placed the lang attribute in the main part of the page, or rather within the ```
<hteml lang="en-uk">
``` of the html document.
The code to modify the displayed content would be easier to handle, you could do something like the following....
```

<!DOCTYPE html>
<html lang="en-uk">
<head>
<!-- your other head content and links to files js / css files here .... -->
</head>

<body>
<iframe src="./{lang}/page.html">
<!-- insert static non language constrained content here if required -->
</frame>
</body>
</html>

```
This feels like a better solution that the initial one, you now just place your specific content into a separate html document, you have a single import to perform, and will send a single page. Also you change only the ```
{lang}</code]part of the src attribute inside the iframe tag.

The downside is that this will take a lot of care and attention to maintain consistency of the structure of the related pages.
I can envisage modifying a page in one language and adding a special div, then the translator arrives you and doesn't notice the new tag and class that you created, and hence the consistency between the presentation for each language begins to drift....

On the other hand it is easy to separate your different languages for your site. You ensure that you use relative links for all your non-text media and the links just stay exactly the same.

Also there is the 'don't use frames' they are bad for search engines' argument.

_Store content in a DB_

This get down to a more grown up solution, but will mean that you site will not work if your server is offline, this makes it less attractive to create pages that are supposed to be viewed offline, forces the use of a more complex server setup, and will add to complication of the scripting that is used - you will likely now need to be using javascript in your pages, and php to collect and serve your data. Ok I know that javascript can communicate with a back end db, but which technology would you use?? Jnode, googleAppScript, WebKit ???

Also there is again the issue of editing the content.

_Content Editor_
So you could roll your whole site with a CMS such as joomla or drupal.

However I like to have a working local version of my site on my local pc,  usefull for peace of mind if the server goes down, or I decide to change your web host, it is easy to just copy all the pages over and to a new server if they are not hooked into a DB and are just flat files.

Also the few Drupal pages that I have used 'wget' to retrieve for friends are a real mess on the local system with various broken links and mutliple embeded Div that make my head hurt.

it's not that I don't appreciate Drupal, it just creates what I feel is an extremely complex structure, for example just for one of the content sections you get the following
[code]
<div class="region region-highlighted">
<div id="block-block-75" class="block block-block">
<div class="block-inner">
<div class="content"
<!-- bunch of content here -->
</div>
</div>
</div>
</div>
 <div class="different section name">
<div id="block-block-75" class="block block-block">
<div class="block-inner">
<div class="content"
<!-- bunch of other content here -->
</div>
</div>
</div>
</div>

```
which too me seems overkill.
Then of course you have the related CSS, with each of at the 3 or 4 pages being 400 odd lines in length. with each one containing different rules for lists and list items etc (or rather the same rules for lists with different classes or ID).

All of which seems far too complex.
OK I'm sure that the creation of the site is vastly more efficient than if I hand code it, but all these files cause the problems in trying to have an effective off-line copy of your site work on.

So my question here is what are other people using to control and manage their multilingual content?
Are there other solutions that I have though about?
Are there any good lightweight html editors (I mostly use geany, but it can't open multiple editing panes) that can be used to open and view / modify multiple files. I would really like a tool that could display my content side by side, or contain a tab for each language that my site has, so I can i mmediately see how many files I need to modify if I add in new content for one specific language - I could easily insert the same content with a [code]visible="false"[code] to keep if from being displayed whilst I get around to translating the required extra content, I would then be able to easily allow visitors to click a button to view the content in their prefered language.

your reflections and thoughts are appreciated in advance.

David

ps. sorry for the long post!

---

### Post by Dimarchi on 2013-12-20
Well, this subject can be such a source of headache it isn't real. :) But! You are on the right track in your musings - and, for what it is worth - what I describe below is not the only way to go about it, nor necessarily the best way.

A quick and dirty way could be something like this, You indicate some way that your site's content can be served in several languages (flags are probably the most common method). Once a user clicks a flag, you save the click flag and the data associated with it to a cookie or session variable (e.g. click English flag, save string "en" to cookie or session variable "language"). The page reloads the language string file and the page in question.
Your page is filled with placeholder strings (scripts, too, where something must be displayed in another language). Example using php:

```
<title><?php echo $hello_string; ?></title>
```

In the language file for English you would have:

```
$hello_string = "Welcome";
```

In the Swedish equivalent for that languuage file you would have:

```
$hello_string = "Välkommen";
```

That $hello_string is the placeholder for the actual string to be rendered in the language selected by the user. If the user wishes to see the page in English, he or she clicks the English flag. The language file and the page is reloaded with English everywhere. Swedish flag for Swedish everywhere. Now, where the problem arises here is the addition of dynamic content and translating that (DOM manipulation). Should I mention dates and all kinds of measures that can mess up things and fast? There are libraries for that purpose, though - the question is do they suit your needs.

That above describes a sort of Poedit way of doing things. And then you can actually use Poedit itself for the absolutely true maximum overkill. I'm not going there. :)

I would refrain from using html lang attribute - it can't be in English if you load content in French. Instead, use meta charset set to utf-8 (for Western languages).

Welcoming comments and corrections.

---

### Post by ju2wheels on 2013-12-20
> **Dimarchi said:**
> I would refrain from using html lang attribute - it can't be in English if you load content in French. Instead, use meta charset set to utf-8 (for Western languages).

Ditto, but scratch the "for Western languages", just use UTF-8 its the best bang for your buck encoding effectively in terms of language support.

You are on the right track with your mapping strings to a language, however most of the time what is done is that people will abstract the strings out of the code into maps organized by language and then just use calls out to wrapper functions to get the right string for the right language as opposed to duplicating code as your example does.

In your example, you also provide a French string example, but note that in languages like Spanish/French one would expect to see characters with diacritics, so its important that when saving your code/text files you save them in UTF-8 (ie dont save in plain text/ASCII, use an editor/IDE that supports encodings or UTF-8 in particular) so that you can use strings with the proper characters.

References:
[http://www.w3.org/International/articles/definitions-characters/](http://www.w3.org/International/articles/definitions-characters/)
[https://www.w3.org/International/questions/qa-choosing-encodings](https://www.w3.org/International/questions/qa-choosing-encodings)

---

### Post by Dimarchi on 2013-12-21
A very good point, that saving in UTF-8. I tend to forget that since I always do it myself, taking it as a given. :)

---

### Post by ofnuts on 2013-12-22
> **ju2wheels said:**
> In your example, you also provide a French string example, but note that in languages like Spanish/French one would expect to see characters with diacritics, so its important that when saving your code/text files you save them in UTF-8 (ie dont save in plain text/ASCII, use an editor/IDE that supports encodings or UTF-8 in particular) so that you can use strings with the proper characters.

The usual encoding (ISO-8859-15 is fine for French and western European languages).Supporting foreign languages isn't always easy, you have to know how far you want to go. I personally grade them thus:


[LIST]
[*]Level 0: American English
[*]Level 1: Other English dialects, Western European languages (supported by default encoding). You stop doing plurals by just adding 's' at the end of things. And sometimes the gender of words (or people) is important.
[*]Level 2: Other languages with a latin alphabet. Besides the need to support more encodings or make sure we are UTF-8 everywhere, you start to hit fun problems, like Turkish, where the uppercase "i" is dotted, and the lowercase "I" isn't, or Croatian where some letters have uppercase, lowercase, and 'titlecase' versions, and some languages that have a 'dual' case besides singular and plural.
[*]Level 3: Alphabet-based languages, written left to right (Greek, Russian, Hindi...). Not much harder than level 2 if you are familiar with the alphabet.
[*]Level 4: Ideographic languages (Classic and Modern Chinese, Japanese, and Korean (which is not truly ideographic). Mostly because even when written horizontally, they wreak havoc in your nicely set layouts, since some things can be a lot shorter, while other things cannot be shortened (you can't make acronyms/initialisms in Chinese).
[*]Level 5: Right-to-left languages (Hebrew, Arabic), aka "Bi-di" (Bi-directional) languages since they often include European words that are kept left to right : your layout should be truly mirrorable left-right (HTML will do that for you if you do it right). Plenty of fun parsing strings. In Arabic vowels are optional, and the same grapheme can have various character representations depending on the position of the character in the word, so word searches can be fun.
[/LIST]

It is also a field laden with politics...

---

### Post by theDaveTheRave on 2014-01-11
Hello again all,

Well it is nice that I am obviously not the only who has thought about this!

@ Dimarchi
> I would refrain from using html lang attribute - it can't be in English if you load content in French. Instead, use meta charset set to utf-8 (for Western languages).

I hadn't thought of that issue, I guess I could however create my own 'tags' such as ```
presentationLang=[english|french|listOfOtherLanguageIDon'tSpeakOrWrite
```.

My real question is if I make a web app, how can I be sure that I can send all the data to the client if they wish to work with it off line (ie the devs, or for backup, or if someone wants to make a translation etc).

For the moment, I am thinking an XML database, that could be sent to the client if reqested.

D

---

### Post by ofnuts on 2014-01-11
The "lang" attribute can be applied to individual HTML elements (paragraphs, etc...)

In a project I did a long while ago, the texts (an ever growing list of car diagnostic and repair actions) were kept in a database, but to send things out to translators (39 languages) we produced a HTML file with a two-columns table, one with the reference language text (French or English, depending on target language) and one with the currently known translation (or nothing). Each table cell had its own "lang" attribute.

The translators would load that file in Word, which, thanks to the appropriate "lang" attribute, would do the spell checking of each cell using the right language. After translation, the files where shown around (local branch people) and eventually sent back to us, and we would parse the table again to populate our DB with the results.

---

