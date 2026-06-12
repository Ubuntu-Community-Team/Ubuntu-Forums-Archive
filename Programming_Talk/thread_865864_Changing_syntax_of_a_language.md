---
title: "Changing syntax of a language"
date: 2008-07-21
forum: Programming Talk
---

### Post by clash on 2008-07-21
Ok guys. 

Heres what I want to do. 

All the english words in a language like for example, C++. I want to change them or more precisely, change them from the point of view of the coder. 

i.e > Coder can write "blah(x < 1)" instead of "if(x < 1)". 

But as far as the compiler knows, its always "if(x < 1)".

Whats the best way to do this ? In an ide and just tell the IDE to convert "blah" to "if" before sending to the compiler ? 

Bare in mind I want to change ALL english words and I might want to use non-latin alphabet characters too. 

Thanks. 

I would prefer to have this independent of a particular IDE.

---

### Post by DavidBell on 2008-07-21
```
#define blah if
```

will do it. Actually ages ago I decided I didn't like C++s curly braces because if you went in too many levels of conditions/loops/etc you couldn't figure out which statement the multiple "}"s linked up to. So I did

```

#define IF if{
#define ELSE }else{
#define ENDIF }

/// etc same for for, while, do etc
/// something like that anyway

```

but never used it, nobody will thank yo for that sort of stuff in the long run.

DB

PS I have seen this in some MS libraries

```
#define TRY something_to_do_with_try
/// etc
```

I think they do it so you can optionally compile out exceptions etc depending on your compiler switches.

---

### Post by slavik on 2008-07-21
look up

#define

but why do you want to do this? (I am assuming you want to translate the if, while, do, etc. into another language?)

---

### Post by clash on 2008-07-21
> **slavik said:**
> look up

#define

but why do you want to do this? (I am assuming you want to translate the if, while, do, etc. into another language?)

Crazy idea I came up with on the subway home. 

My "theory" is that non-english native speakers would feel more comfortable reading&writing code when they can use their own languages words.

---

### Post by slavik on 2008-07-21
see davidbell's response :)

---

### Post by Quikee on 2008-07-21
> My "theory" is that non-english native speakers would feel more comfortable reading&writing code when they can use their own languages words.

I am a non-english speaker and it would bother me greatly reading and writing code in my own language (or any other language) instead. Even things like comments / descriptions and variable names should never be in non-english especially if you ever want to paste the code on a international forum or share it with other people on the internet.

---

### Post by shifty2 on 2008-07-21
Even being british, I take the time to try and write my code in US english to make it more consistent. 

Of course, if the code is just for personal use there is no real reason not to write comments in your own language - beware of changing the syntax though as they are effectively learning a different language.

---

### Post by dribeas on 2008-07-21
> **clash said:**
> Crazy idea I came up with on the subway home. 

My "theory" is that non-english native speakers would feel more comfortable reading&writing code when they can use their own languages words.

Please don't. Microsoft went that way with their office suit, and even there it makes more sense, and it becomes a real problem later on. The user can say: SI (condition) {} SINO {}, as an example in spanish, and that may be a little easier on the very short term. But then she will want to get help from internet forums, google code, books, friends... and she will run into the nightmare of having to translate.

That is the case with, say excel, where you can read in forums how to do anything, but then depending on the installed version it may work or not, or you will need to get a dictionary, find other wordings, search through help to find the correct wording for your version...

While it is close to english language, the important part is that programming language are precise and simple, and there are just so many constructs to learn (20-30 reserved words in real languages?) Or do you really want to translate every library?

BTW: using #define's might work, but then you are making the compiler translate every occurrence of the word by your definition which might be confusing at cases, and if any library source you try to include has any of those words then the user will have traded the difficulty of learning 'if' with compiler errors on code she has not even written.

---

### Post by clash on 2008-07-21
Hey guys, I fully understand and agree with almost everything that has been stated. 

I don't think I explained myself well .... or maybe I did. 

scenario. 

Jack is Chinese. Jack gets some C++ code from a forum and wants to read through it. Jack opens it up in his IDE and its displayed in its "original" english. 

Jack decides he wants to read it in Chinese so clicks a button (Or his IDE automatically displays in Chinese, whatever) and all the english-y keywords are changed to chinese, using chinese characters. 

If Jack makes changes to the code, he can make it in Chinese. So Jack saves it and uploads his code onto the forum.  

Bob is English and downloads Jacks new code. But because Bob's IDE knows Bob speaks english it just displays the code in english. 

Regardless, the code will always be saved etc in its original english because thats what the compiler understands. 

I don't want to change a language, I want to add a layer for readability. The code will always be in its original spec form. 

This is just a preference thing I'm talking about ...

Or I'm just raving mad. 

Opinions ?

---

### Post by dribeas on 2008-07-21
That seems as IDE-dependent. You would need to write a plugin for the IDE you use such that the translation is done in one direction while reading and the opposite while writting. Again you do run into the same problems. Say you have the following code (english):

```

if ( si ) { // si stands for single-impact in this shoot-them-up game
   ...
}

```

and a user loads into a spanish:

```

si ( si ) {
   ...
}

```

Now it will be quite interesting to switch back to english, which 'si' must and which must not be translated?

And that is just the simplest example I figured.

---

### Post by pmasiar on 2008-07-21
> **clash said:**
> My "theory" is that non-english native speakers would feel more comfortable reading&writing code when they can use their own languages words.

I see you live in Ireland: do you speak Irish? Did any non-English **programmer** ever asked for that? I doubt it. Maybe some very green beginner lives with illusion that having translated keywords would speed up learning, but that's only illusion.

Take me as an example: English is not between my first three languages, but I still preferred English keyword back then when I was only beginner in English, and found translated keywords confusing.

In fact, couple dozen of English keywords is trivial to learn and not any impediment in understanding the program: main problem is understand control flow and data transformations, and translated keywords are useless for that.

If anyone, wants to go to international forums,  understanding basic English is given. On local forums, comments in native language help to bridge the gap. 

IMHO such feature will be rarely if ever used, and would be ignored by non-beginners, so you would have hard time to build developer community around it. And without community, it would be not promoted but ignored, it's hard to  fight against such feedback loop.

---

### Post by clash on 2008-07-21
> **pmasiar said:**
> I see you live in Ireland: do you speak Irish? Did any non-English **programmer** ever asked for that? I doubt it. Maybe some very green beginner lives with illusion that having translated keywords would speed up learning, but that's only illusion.

Oh no, nobody ever asked for it. 

My "theory" is actually based on natural language. i.e > People feel more comfortable reading and writing their own language. 

I'm actually working in South Korea at the moment teaching kids English for a year and even though many of them are perfectly fluent in English, they still feel far more "comfortable" using their own languages words even for the most simple of things. 

I know that writing code and writing an essay in an actual language are completely different things. Its just something I was interested in looking into. 

i.e > 

Is it easier/more comfortable for a Korean programmer to read: (display of asian languages needed)

if (x > 10) {
  a = 'foo';
}

or 

&#47564;&#50557; (&#12610; > 10) {
   &#50500; = '&#54620;';
}


Please understand when I say that I in no way mean that this would make a "big" difference whatsoever. But I do believe that it would make a small difference for non-native speakers when reading code. 

I know when I see another languages word I automatically convert it to English in my mind no matter how long I've learned the language or how many times I see that word. 

Do you do the same ? 

What about using this in something like natural language processing ? As opposed to something like C++/Java etc

---

### Post by LaRoza on 2008-07-21
> **clash said:**
> 
My "theory" is actually based on natural language. i.e > People feel more comfortable reading and writing their own language. 
Where are these people?

> 
Is it easier/more comfortable for a Korean programmer to read: (display of asian languages needed)
No. Look at Ruby ;)

> 
I know when I see another languages word I automatically convert it to English in my mind no matter how long I've learned the language or how many times I see that word. 

Do you do the same ? 
No, I try to see it as the concept. Those who have mastered other languages, seem to do the same. Even in my efforts to learn Hindi (not that old, less than a week) I see things in Devanagari (see title)

---

### Post by clash on 2008-07-21
> **LaRoza said:**
> Where are these people?

Everywhere ? 

My better half is Korean and she is perfectly fluent in English but still finds it more comfortable to read Korean then English. Shes perfectly capable of reading English but its a "comfort" thing. 

> No. Look at Ruby ;)

fair enough :P

> No, I try to see it as the concept. Those who have mastered other languages, seem to do the same. Even in my efforts to learn Hindi (not that old, less than a week) I see things in Devanagari (see title)

Yes those who have mastered the language. How many Chinese/Korean/Indian etc programmers have mastered English ?

---

### Post by LaRoza on 2008-07-21
> **clash said:**
> Everywhere ? 
I thought you meant programming. Programming terms don't have meaning like English/$LANG words do. The concepts are what are important and the use of English is standard (even non native speakers do it) in programming.

> 
My better half is Korean and she is perfectly fluent in English but still finds it more comfortable to read Korean then English. Shes perfectly capable of reading English but its a "comfort" thing. 
Programming is different.

> 
Yes those who have mastered the language. How many Chinese/Korean/Indian etc programmers have mastered English ?

You don't have to know the language to use it. The words don't matter and are easily learned. "if" becomes a conditional phrase, independent of its actual meaning.

While it may be a fun excercise, it wouldn't be that useful. Think about it...if there were a demand for it, it would have been done already (it is trivial to change the keywords, a simple .h file could render C in any language).

---

### Post by clash on 2008-07-21
> **LaRoza said:**
> I thought you meant programming. Programming terms don't have meaning like English/$LANG words do. The concepts are what are important and the use of English is standard (even non native speakers do it) in programming.

I said my theory comes from "natural language". 

> Programming is different.

Indeed it is and I didn't say it wasn't. But when you have not mastered a language it is always easier to use your own. 

Especially when you are talking about people familiar with non-latin characters. Their own characters just look more "normal". 

> You don't have to know the language to use it. The words don't matter and are easily learned. "if" becomes a conditional phrase, independent of its actual meaning.

Imagine your a first year University student in Japan/India etc and you are been taught about for loops. You don't speak English. Whats going to be easier for you ? the english "if" or the indian/Japanese word ? 

> While it may be a fun excercise, it wouldn't be that useful. Think about it...if there were a demand for it, it would have been done already (it is trivial to change the keywords, a simple .h file could render C in any language).

You'd be surprised how much impact the smallest things have. 

Look at UI design. 

So how do I get GCC to accept non-latin alphabet characters ? Because I just tried #define there about it was happy with changing if to a latin based word but not to asian characters.

---

### Post by stevescripts on 2008-07-21
Since you mentioned that your better-half is Korean (as is my own), that explains your choice of hangul for your example.

That said, take a look at this link: 
(edited out, see below)

Your korean may be up to technical discussions in Korean, but, even after 37+ years, I certain know that *mine* isn't ...

Looking about on the language forum of your choice may be enlightening, when it comes to things like keywords.

Steve
link is long did not copy right - try again below
[http://groups.google.com/group/news.admin.hierarchies/browse_thread/thread/ec8ba7773fcc5354/8cc3048d4920592c?lnk=st&q=korean+language+tcl+forum#8cc3048d4920592c](http://groups.google.com/group/news.admin.hierarchies/browse_thread/thread/ec8ba7773fcc5354/8cc3048d4920592c?lnk=st&q=korean+language+tcl+forum#8cc3048d4920592c)

---

### Post by clash on 2008-07-21
> **stevescripts said:**
> Since you mentioned that your better-half is Korean (as is my own), that explains your choice of hangul for your example.

That said, take a look at this link: 
(edited out, see below)

Your korean may be up to technical discussions in Korean, but, even after 37+ years, I certain know that *mine* isn't ...

Looking about on the language forum of your choice may be enlightening, when it comes to things like keywords.


Thanks Steve but my korean is more or less non-existant unless I'm asking for a beer or cigarettes :)

I've been living in Seoul for 8 months and only made an effort to learn the language in the last 3-4. 

I might get the better half to send a request though. Thanks :)

---

### Post by LaRoza on 2008-07-21
> **clash said:**
> 
Especially when you are talking about people familiar with non-latin characters. Their own characters just look more "normal". 
After one week, Devanagari is natural to me, even when I don't know the words.

> 
Imagine your a first year University student in Japan/India etc and you are been taught about for loops. You don't speak English. Whats going to be easier for you ? the english "if" or the indian/Japanese word ? 

For the concept? My native language. For the source? What is standard.

> 
You'd be surprised how much impact the smallest things have. 

Perhaps. But I know of one language that isn't in english and it is a proprietary and highly specific language (in French).

> 
So how do I get GCC to accept non-latin alphabet characters ? Because I just tried #define there about it was happy with changing if to a latin based word but not to asian characters.

Not sure. I will look into it.

---

### Post by clash on 2008-07-22
> **LaRoza said:**
> After one week, Devanagari is natural to me, even when I don't know the words.

Than your a better/smarter man then me because I have been learning korean for 4 months and hangul still looks "foreign" and "strange". 

> 
Not sure. I will look into it.

Thanks :)

---

### Post by pmasiar on 2008-07-22
> **clash said:**
> Imagine your a first year University student in Japan/India etc and you are been taught about for loops. You don't speak English. Whats going to be easier for you ? the english "if" or the indian/Japanese word ? 

I do not have to imagine, I was there: I learned programming way before I was able to read even simple English (beyond beginner's textbook). 

And let me tell you, english keywords are not a problem. What beginner want is to name variables in own language, and I explained you before - and this is from experience. Including (bad) experience with programming MSFT Excel macros in 'naturalized' language: it was total flop, people were willing to pay more for English version, instead of cheaper translated.

And for variable names, native alphabet is nice but not necessary: all languages have commonly used transliteration to ASCII, just use it. Human brain is extremely flexible and will cope with it, because deeper problems are harder to solve: imagine states of computer in loop, dynamic data structures etc (where no translation is needed).

Trust me, this is true for any problem: if it was not solved already, most likely it is **NOT** a problem for any significant group of people. Finding interesting and useful niches is hard. If it is not solved, someone already is working on it, and is better join.

---

### Post by LaRoza on 2008-07-22
> **clash said:**
> Than your a better/smarter man then me because I have been learning korean for 4 months and hangul still looks "foreign" and "strange". 


Perhaps Devanagari is simpler? I don't know anything about Korean.

> 
Thanks :)

I can't get it to work. I can use Unicode (Devanagari in this case) as #define's, but not to replace keyboards. It seems the compiler can't handle it. I don't know of a way to get around that, unless you were to recompile gcc with unicode support, which I don't know if it is possible. The best I can recommend is writing a preprocessor for a language to convert it to its normal code.

---

### Post by stevescripts on 2008-07-22
A short cut'n'paste from han.comp.lang.c
```

&#50500;&#47000; &#53076;&#46300;&#50640;&#49436; test_t&#53440;&#51077;&#51012; &#48372;&#47732; unsigned char&#53440;&#51077;&#51004;&#47196; &#48708;&#53944;&#54596;&#46300;&#47484; &#51221;&#51032;&#54664;&#49845;&#45768;&#45796;.
&#44536;&#47088;&#45936; Little Endian&#44284; Big Endian&#51012; &#49324;&#50857;&#54616;&#45716; CPU&#50640;&#49436; &#44033;&#44033; &#45796;&#47480; &#44208;&#44284;&#44032; &#45208;&#53440;&#45225;&#45768;&#45796;.
(&#47592; &#50500;&#47000; &#52636;&#47141; &#48512;&#48516; &#52280;&#51312;)
Little&#50640;&#49436;&#45716; test_t&#53440;&#51077;&#45236;&#51032; d1&#51060; LSB&#47196; &#44032;&#45716;&#45936;, Big&#50640;&#49436;&#45716; MSB&#47196; &#44032;&#45716; &#44163; &#44057;&#49845;&#45768;&#45796;.
1&#48148;&#51060;&#53944;&#45236;&#50640;&#49436;&#51032; &#48708;&#53944; &#49692;&#49436;&#44032; &#50780; Endian&#44284; &#44288;&#44228;&#44032; &#51080;&#45716; &#51648;&#47484; &#47784;&#47476;&#44192;&#49845;&#45768;&#45796;.
C&#54364;&#51456;&#50640;&#49436; &#48708;&#53944;&#54596;&#46300;&#51032; &#50948;&#52824;&#44032; &#50612;&#46523;&#44172; &#51221;&#51032;&#54616;&#44256; &#51080;&#45208;&#50836;?

&#52628;&#49888;: &#50836;&#51608;&#51008; &#50612;&#46500; &#44228;&#51221;&#51004;&#47196; &#45684;&#49828;&#44536;&#47353;&#51012; &#51217;&#49549;&#54616;&#45208;&#50836;?
      "news.kreonet.re.kr"&#47196; &#51217;&#49549;&#51060; &#50504;&#46104;&#45348;&#50836;...&#12636;.&#12636;

////////////////////////////////////////
#include <stdio.h>
#include <string.h>

typedef struct {
        unsigned char d1 : 1;
        unsigned char d2 : 7;

} test_t;

int test()
{
        test_t tmp;
        char buf[1];

        memset(&tmp, 0, sizeof(tmp));
        memset(buf, 0, sizeof(buf));

        tmp.d1 = 1;
        buf[0] = 1; 

```

I was more than slightly amazed by the amount of spam that makes it into the Korean newsgroups, but, as this shows, the language used to program is english.

See again what pmasiar says ... He has a point (and he most often does)

Steve

---

### Post by clash on 2008-07-22
Ok ... So my latest daft idea is this.

I want to develop a new "language" based on high level psuedocode.

e.g >

**if** credit card number **is valid then**
    **execute** transaction
**else**
    **show** a card invalid error
[B]end if
[/B]

So you would write your code in this psuedocode. There will still be keywords etc and it still requires a certain syntax. Its not natural language.

But after you write a program in this psuedocode, you can convert(save it as) a choice of C++/Java etc code.

You can write this psuedocode in any language (English, Korean etc) but when you want to actually use the code it will be converted into standard C++/Java/C# etc.

So in actual fact you could write. (English)

**if** number **is valid** ....

or (Korean) (asian language support installed ?)

**&#47564;&#50557;** &#49688; **&#51221;&#54869;&#54620;** ....

or more like C code

if (x < 10){
   "hello"
}

&#47564;&#50557;(&#12610; < 10){
  "&#50504;&#45397;"
}

And the program will be able to convert this from very high human readable (any language supported) psuedocode into C++/C#/Java code.

So am I mad ? 

Anyone going to call the men in white coats for me ?

---

### Post by nvteighen on 2008-07-22
Ugh... Time for the invited philology-student:

I'm currently translating a text from German to Spanish (or I should be doing it instead of writing in these forums); what I'm doing is to take some information expressed in one code-system (German) and drop it into another one (Spanish) that way that the less information is lost (there's always a loss when translating) and the resulting text is correct and natural in the target language.

OK. E.g., you want to take C and replace:
```

if(a == 1)
    return 0;
else
    return 4;

```

By (Spanish):
```

si(a == 1)
    regresar 0;
si no
    regresar 4;

```

Problems: "si no" are two words ("sino" means something else), "regresar" is a litteral translation for "return"... but sounds terrible in Spanish, in which the verb is more used for movements (as in "I returned to home" = "Regresé a casa").

Translating keywords would suppose to attempt giving an English meaning to a non-English word... as you'll be restricted to 1:1 translation. The result, paradoxically, will be more unnatural than what you have now, IMO. Only too specific, scientific (and actually artificial) words are cross-language...

So, developing a whole programming language from a different language seems to be more sane. The issue is whether that's pragmatically useful or not, I mean: if the community will be willing to accept that... But the only way to check that will be to try it.

---

### Post by clash on 2008-07-22
> **nvteighen said:**
> 
OK. E.g., you want to take C and replace:
```

if(a == 1)
    return 0;
else
    return 4;

```

By (Spanish):
```

si(a == 1)
    regresar 0;
si no
    regresar 4;

```

Problems: "si no" are two words ("sino" means something else), "regresar" is a litteral translation for "return"... but sounds terrible in Spanish, in which the verb is more used for movements (as in "I returned to home" = "Regresé a casa").

Translating keywords would suppose to attempt giving an English meaning to a non-English word... as you'll be restricted to 1:1 translation. The result, paradoxically, will be more unnatural than what you have now, IMO. Only too specific, scientific (and actually artificial) words are cross-language...

Hey man thanks for the feedback.

But. 

Why would i be restricted to 1:1 translation ? 

What I'm talking about would be having a Spanish/etc word that is the equivalent of what "return" means in the context of a C program. It doesn't need to be a literal dictionary translation of the English word "return".

---

### Post by nvteighen on 2008-07-22
> **clash said:**
> 
Why would i be restricted to 1:1 translation ? 

What I'm talking about would be having a Spanish/etc word that is the equivalent of what "return" means in the context of a C program. It doesn't need to be a literal dictionary translation of the English word "return".

You'll be restricted to 1:1 translation because you're translating concepts just changing the "label", not considering all other aspects in language that also convey information: syntax, relationships between words (the "difference" a word with respect to all others in the language is what counts, according to Saussure), morphology and context... The problem is related to the fact that programming languages are not like natural languages.

Yes, in some cases, it may work, but not in all. "Return" in Spanish is good example on this: "regresar" would be litteral... Maybe "devolver" ("to give back")? But then you're missing the idea that you're returning to the caller function... "Return" in English englobes both meanings of "come back" and "give back" just in one word.

But also: "if" in English may only be translated in languages that actually recognize conditionals as a syntactic structure, though it can express conditions somehow (an inflected participle, as you can do in Latin or Greek...) I don't know any real example on that, but something like that could exist in theory... (To understand what I mean: you can express lists both in C and in Python, but only the latter recognizes it as part of its syntax, while the former needs a workaround for that).

This should be more dramatic in non-related languages as English and Korean. You may encounter much less troubles between English and Danish (believe me), but you'd still have some...

---

### Post by LaRoza on 2008-07-22
> **clash said:**
> 
I want to develop a new "language" based on high level psuedocode.

e.g >

**if** credit card number **is valid then**
    **execute** transaction
**else**
    **show** a card invalid error
[B]end if
[/B]

Already been done. Python :-) Or if you want to be evil, Cobol. The verbosity isn't a good thing.

> 
So am I mad ? 

Considering that most people here are, it would be no surprise.

> 
Anyone going to call the men in white coats for me ?

Black coats, and they don't exist...

---

### Post by pmasiar on 2008-07-22
> **clash said:**
> 
**if** credit card number **is valid then**
    **execute** transaction
**else**
    **show** a card invalid error
[B]end if
[/B]

So you would write your code in this psuedocode. There will still be keywords etc and it still requires a certain syntax. Its not natural language.


...but it looks close to Python :-) And as I said, Python has option to use non-ascii characters in comments and IIRC also in variable names, that's all you really need trust me.

---

### Post by mssever on 2008-07-22
Apple tried this years ago with HyperCard. They tried to create a language that was as close to natural English as possible. But syntax isn't the hard problem of programming, and I doubt that HyperCard had any significant effect on programming because of it's natural language syntax.
> **clash said:**
> Than your a better/smarter man then me because I have been learning korean for 4 months and hangul still looks "foreign" and "strange".
This raises another interesting point: I think some scripts are easier to learn than others, based on what a person is already familiar with. For example, when I studied Greek, I became fluent in the script (but not the language) very quickly, and I can read the Greek script as quickly as the Latin script. However, when I studied Hebrew, I never became as comfortable with that script, because the Hebrew script is unlike any other script I know. And even though I don't speak a word of any language that's written with the Cyrillic script, I can handle the script itself without too much difficulty by making analogies between the Greek, Hebrew, and Latin scripts. I don't know much about Devangari, but I did read about it on Wikipedia when LaRoza put it in her signature. It's different from the other scripts I know, but Hangul is also quite a different concept--especially if you mix in the occasional Chinese character.

But I wonder know whether your difficulty with Hangul actually works both ways. The Latin script is so pervasive that most people have some familiarity with it already. The Russian keyboards we had at one place I worked had Latin labels in addition to the Cyrillic. Until recently, DNS was limited to ASCII. System filenames typically aren't localized. So I'm guessing that computer-savvy Koreans are already familiar with the Latin script to some extant, even if they don't know English. (I even understand that the most popular way to type in Japanese is by typing the Romanized transliteration and having software do the translation to Japanese characters.)

---

### Post by LaRoza on 2008-07-23
> **mssever said:**
> 
I don't know much about Devangari, but I did read about it on Wikipedia when LaRoza put it in her signature. It's different from the other scripts I know, but Hangul is also quite a different concept--especially if you mix in the occasional Chinese character.
It is actually quite simple. Each character has one sound, and one sound only. Devanagari is used for many languages, and could even be used for English. The characters are "hanging" from a line. There is no such thing

The only confusing part for someone not used to it would be the maatraas, which are just a second form of a vowel when it follows a consonant (each letter has an implied vowel sound, so many words have no written vowels).

> 
 The Russian keyboards we had at one place I worked had Latin labels in addition to the Cyrillic. 
Indians don't even have Devanagari keyboards!

---

### Post by mssever on 2008-07-23
> **LaRoza said:**
> There is no such thingAs what?
> Indians don't even have Devanagari keyboards!So do they type in transliteration, or just memorize a character map?

I just checked, and Gnome's Indian default keyboard layout looks like it would work for Devanagari.

---

### Post by LaRoza on 2008-07-23
> **mssever said:**
> As what?

...as upper and lowercase letters. I guess that is what happens when you are not writing the post in order :-)

> 
So do they type in transliteration, or just memorize a character map?
If you use a quality browser and go to [http://hi.wikipedia.org](http://hi.wikipedia.org) and type in the search box, you'll see it automatically become Devanagari. If you use Fx, go to:

[http://www.google.com/transliterate/indic](http://www.google.com/transliterate/indic)

(Considering one doesn't look at the keyboard when typing it, it really isn't that hard)

> 
I just checked, and Gnome's Indian default keyboard layout looks like it would work for Devanagari.
Is there a way to change back and forth?

---

### Post by nvteighen on 2008-07-23
> **LaRoza said:**
> 
Is there a way to change back and forth?

Yes, there's a panel applet that allows you to change layouts and also keep different layouts for each different window.

---

### Post by LaRoza on 2008-07-23
> **nvteighen said:**
> Yes, there's a panel applet that allows you to change layouts and also keep different layouts for each different window.

I don't use GNOME, but I'll have to try it.

---

### Post by mssever on 2008-07-23
> **LaRoza said:**
> Is there a way to change back and forth?
I've configured the keyboard applet to switch layouts whenever I hit scroll lock (finally, a use for that key). I used to use <Shift>CapsLock on my old machine, but for some reason my new machine doesn't like switching based on <Shift>CapsLock.

Given the frequent font warnings on sites using indic text, and given that Devanagari keyboards don't exist apparently, does that mean that proper font rendering is a hard problem that wasn't solved until comparatively recently?

---

### Post by LaRoza on 2008-07-23
> **mssever said:**
> I've configured the keyboard applet to switch layouts whenever I hit scroll lock (finally, a use for that key). I used to use <Shift>CapsLock on my old machine, but for some reason my new machine doesn't like switching based on <Shift>CapsLock.
Scroll lock is used by my kvm (but has to be hit twice rapidly). I'll try to get it set up later.

> 
Given the frequent font warnings on sites using indic text, and given that Devanagari keyboards don't exist apparently, does that mean that proper font rendering is a hard problem that wasn't solved until comparatively recently?
The keyboards "exist", but so do honest lawyers. Good luck finding one.

I know they almost all use Latin (Hindi-Urdu uses two very different ways of writing, but both can use Latin characters) at least a little bit, to the extent my asking them how to get Devanagari was answered with "I don't know, let me know if you find out".

For typing it, they all seem to use software.

---

### Post by nvteighen on 2008-07-23
I still wait for a decent keyword support for Ancient Greek... in any OS... I have to rely on a proprietary font for that. There are open source alternatives, but still too useless to be used in professional work (at least those which I know).

---

### Post by mssever on 2008-07-23
> **nvteighen said:**
> I still wait for a decent keyword support for Ancient Greek... in any OS... I have to rely on a proprietary font for that. There are open source alternatives, but still too useless to be used in professional work (at least those which I know).

As far as fonts go, GentiumAlt is awesome for &#954;&#959;&#953;&#957;&#951; Greek; I don't know whether it contains the additional letters that are necessary for classical Greek. I had a great &#954;&#953;&#959;&#957;&#951; keyboard layout in Windows running under the freeware version of Keyman. Under Linux, life isn't so great in that regard. The layout I'm using doesn't seem to like accents. There is a polytonic layout available, but when I have it in my list of available layouts, it breaks dead keys on all my installed layouts.

---

### Post by LaRoza on 2008-07-23
> **nvteighen said:**
> I still wait for a decent keyword support for Ancient Greek... in any OS... I have to rely on a proprietary font for that. There are open source alternatives, but still too useless to be used in professional work (at least those which I know).

Ancient Greeks didn't use computers a lot, so they are a couple thousand years behind in development...

A big issue with Devanagari would be with type writers. Latin characters are easy, they go in a row. Devanagari does that also, but have conjucts (a way of sticking two letters together to cancel the implied vowel sound) and they are easy to read, but would be very hard to do mechanically in any usable way.

---

### Post by nvteighen on 2008-07-24
> **LaRoza said:**
> Ancient Greeks didn't use computers a lot, so they are a couple thousand years behind in development...

Yup. But I do use a computer and I'm required to type Greek on it... :p

---

### Post by LaRoza on 2008-07-24
> **nvteighen said:**
> Yup. But I do use a computer and I'm required to type Greek on it... :p

You are either a student of Greek, Greek, or a mathematician...

---

### Post by nvteighen on 2008-07-24
> **LaRoza said:**
> You are either a student of Greek, Greek, or a mathematician...

First of three. (I'm a Philology student, mostly leaned to Linguistics, but have some love for Classical Languages).

A Modern Greek doesn't need to type "spiritus" (aspiration signs) nor spiritus+accents (acute, grave or circumflex...) nor any "iota subscripta" (a little non-pronounced "i" placed **below** a long vowel...) as an Ancient Greek would have needed.

The Ancient Greek script is a diacritic hell. There are words (a verb, e.g.) consisting on a vowel and three diacritic signs.

---

### Post by LaRoza on 2008-07-24
> **nvteighen said:**
> First of three. (I'm a Philology student, mostly leaned to Linguistics, but have some love for Classical Languages).

"Philology" == "Knowledge (study) of Phil"

> 
A Modern Greek doesn't need to type "spiritus" (aspiration signs) nor spiritus+accents (acute, grave or circumflex...) nor any "iota subscripta" (a little non-pronounced "i" placed **below** a long vowel...) as an Ancient Greek would have needed.

Luckily, Hindi has its own letters for aspirated sounds.

> 
The Ancient Greek script is a diacritic hell. There are words (a verb, e.g.) consisting on a vowel and three diacritic signs.
That sounds fun :-) Hindi has a few one letter words (letters are entire syllables), and maatraas can look like parts of the letter (see last word in my title, it is two letters, but the maatraa (vowel) is positioned in a way that makes it look like it is part of it)

---

### Post by nvteighen on 2008-07-24
> **LaRoza said:**
> "Philology" == "Knowledge (study) of Phil"

Yes, I know Phil a lot. A nice guy. :p

> That sounds fun :-) Hindi has a few one letter words (letters are entire syllables), and maatraas can look like parts of the letter (see last word in my title, it is two letters, but the maatraa (vowel) is positioned in a way that makes it look like it is part of it)

Yes, Greek is much more fun than Latin... The later is too "mathematical", too strict in syntax, too previsible... plain, after all. Greek is a "mess" as the word order is extremely flexible, but that leads to immense creativity. Ah, and Greek is more related to Sanskrit and other languages from India than you might think!

(Oh, I'm pushing one of the philological flamewars! Hopefully there's no latinist in here...)

Probably Perl resembles Greek?

---

### Post by LaRoza on 2008-07-24
> **nvteighen said:**
> 
Yes, Greek is much more fun than Latin... The later is too "mathematical", too strict in syntax, too previsible... plain, after all. Greek is a "mess" as the word order is extremely flexible, but that leads to immense creativity. Ah, and Greek is more related to Sanskrit and other languages from India than you might think!

When I was beginning programming, I was in Borders and a guy told me that. We were in the programming books section, and he was trying to find a more modern language for his work (he used BASIC). I told him I was more familiar with Latin...

> 
Probably Perl resembles Greek?

No, Perl resembles all the adults in Charlie Brown ;)

---

### Post by mssever on 2008-07-24
> **nvteighen said:**
> A Modern Greek doesn't need to type "spiritus" (aspiration signs) nor spiritus+accents (acute, grave or circumflex...) nor any "iota subscripta" (a little non-pronounced "i" placed **below** a long vowel...) as an Ancient Greek would have needed.
   
   The Ancient Greek script is a diacritic hell. There are words (a verb, e.g.) consisting on a vowel and three diacritic signs.
   Funny how a (presumably) Latin term, spiritus, is used to describe the Greek breath marks. I don't know the proper Greek name, but I assume it'd be related to &#960;&#957;&#949;&#965;&#956;&#945;. The freeware font Mounce can easily handle accents, breathing marks, iota subscripts, etc. But it isn't a unicode font; it merely changes the glyphs of the latin range.
  
  
  Unicode fully supports ancient Greek, and there are several quality fonts that do, as well. If I can find out how to create a keyboard layout, maybe I'll work up something for Linux (or at least Gnome--I don't know if there's a difference).
  
  Supporting polytonic Greek shouldn't be difficult; I guess there's just not too much demand for it anymore.
 
 EDIT: The bigger challenge for me was when I first was studying Hebrew. I was running Red Hat 7.3 at the time with OpenOffice 1.0, which didn't have right-to-left language support. I had to type all my assignments in reverse, just so I could make them print correctly. That was a chore!

---

### Post by nvteighen on 2008-07-25
> **mssever said:**
> Funny how a (presumably) Latin term, spiritus, is used to describe the Greek breath marks. I don't know the proper Greek name, but I assume it'd be related to &#960;&#957;&#949;&#965;&#956;&#945;. The freeware font Mounce can easily handle accents, breathing marks, iota subscripts, etc. But it isn't a unicode font; it merely changes the glyphs of the latin range.

It is *pneûma*, but traditionally grammar terms are always given in Latin.

> Unicode fully supports ancient Greek, and there are several quality fonts that do, as well. If I can find out how to create a keyboard layout, maybe I'll work up something for Linux (or at least Gnome--I don't know if there's a difference).
  
Supporting polytonic Greek shouldn't be difficult; I guess there's just not too much demand for it anymore.

GNOME does support Polytonic Greek and there is a layout, the problem is Ubuntu's (or maybe even Debian's) default locale configuration. There's an obscure trick compositing the locales that works sometimes. Search in the forums... there's even a thread started by me on this, if I remember well.

The issue is that I also need some other obscure functionalities very specific to Philological studies: e.g. vowel length marks (macron and micron), deprecated symbols (sampi, stigma, koppa: the three "lost" letters) and other stuff that are not part of the alphabet, but used in papers.

Nope, probably there isn't a major demand on this... :p

> EDIT: The bigger challenge for me was when I first was studying Hebrew. I was running Red Hat 7.3 at the time with OpenOffice 1.0, which didn't have right-to-left language support. I had to type all my assignments in reverse, just so I could make them print correctly. That was a chore!

Ugh...

---

### Post by simosx on 2008-10-24
In Ubuntu 8.10, you should be able to write Greek Polytonic simply by enabling the Greek Polytonic layout from the Keyboard settings. It will not matter which locale you have, it should just work (tm).

Note that this relates to Ubuntu and specifically to GTK+ applications, such as OOo, Firefox, all of GNOME.

If a problem with Greek Polytonic persists in 8.10, feel free to pester me (pm, or reply here).

---

