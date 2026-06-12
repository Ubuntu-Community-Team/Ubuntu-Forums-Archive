---
title: "wanna participate in ubuntu developement"
date: 2007-09-14
forum: Programming Talk
---

### Post by yestalk on 2007-09-14
don'n know how to participate in ubuntu developement with my english level and my progarmm skill, does any one could led me to do those cool things?


both kernel or motu could be insteresting.

my level

a little english

a little java(more)

javascript

design pattern

-----------------------------------------------

hate  bash coding , if there is some gluewater which glue separate appliction to cooperate together. an javascript like language shoud be prefer.


really want to know about assembly,know the hardware.


so , is there any one  or resource  to anatomise ubuntu how to work?

thanks.

---

### Post by pmasiar on 2007-09-14
you can translate ubuntu to your native language

Other than that, pick any project you like and want add a feature, and dive in!

---

### Post by yestalk on 2007-09-14
i,just can't find the document to translate.

for example

how tcp/ip work , for java knowledge,we just know about interface(interface maybe enough for app to control some detai,may not.l)

socket = serverSocke.accept();

newthread(socket);

this all i can't control in my app , in many toturial it is.....

how about dns ?

i just know its port number is 25 ?

is there any planform for pure logic? and those logic could run in interpret mode or binary mode.

exactly , i don't understand the architecture of ubuntu or linux. how can i find those doc for esay to study?

thanks.

---

### Post by CptPicard on 2007-09-14
I've seen some confused posts here, but this takes the cake.. I mean, wtf? :)

---

### Post by yestalk on 2007-09-14
:lolflag:so confuse i am........................................................:confused:

---

### Post by Tomosaur on 2007-09-14
> **yestalk said:**
> :lolflag:so confuse i am........................................................:confused:

Ok, back up a little bit!

What is your experience so far? Have you ever programmed anything before? What languages do you know?

The Linux kernel is written in C / C++.

Applications can be written in anything you like - Ubuntu favours Python, however.

The website you need is [Launchpad](http://www.launchpad.net). That's where Ubuntu developers hang out - and is your first stop if you want to work on something Ubuntu specific.

However - most people will just find an application they like, and go to that project's website and find out how to get hold of the source code. Then they can make their own changes and submit their patch back to the core development team.

---

### Post by Compyx on 2007-09-14
One of the great strengths of Linux is portability, so using assembly would pretty much defeat that purpose. Perhaps some very specific code that addresses hardware (drivers) uses assembly, but generally you should stay away from assembly if you want to keep your code portable and thus useful for others.

AFAIK, the Linux kernel is written in C, probably GNU-C, but kernel development isn't for the faint of hearted.

Generally applications are written in C or C++ (there is no 'C/C++') and a host of other languages, both compiled and interpreted. Many Ubuntu-specific tools seem to be written in Python (many Gentoo tools too), so perhaps you could look into learning Python.

The best way to learn a language and it's libraries is first to learn to write portable (using only standard libaries) code and once you've mastered that looking into using non-standard libraries (such as Gtk+, ncurses, etc).

---

### Post by yestalk on 2007-09-14
maybe you are right, i don't know cpp totaly. it's hard than java ,but i also think java could not control hardware,so she could not use to write a os.

and the java is too restrice,

for example:

public class MailAddress
{
   private String userName;
   private URL url;
    MailAddress(String mailaddr)
   {
         this.userName = mailaddr.subString(0,mailaddr.indexOf("@"));
         this.url = new URL(mailaddr.subStirng(mailaddr.indexOf("@")+1,mailaddr.length-1));
   }
   public URL getAddr()
{
   return this.url;
}
  public String getUserName()
{
    return this.userName;
}
}
 public class A
{
    
    setEmailAddress(EmailAddress mailaddr)
   {
        //i know the mailladd must be a EmailAddress.
        //so, i can do this:
        
        maybeCheckForIP(mailaddr.getAddr());
        maybeCheckForUserName(mailladdr.getUserName());
   }
}


public class TestUsage
{

   public static void main(String[] args)
  {
       (new A ()).setEmailAddress(args[0]) ; // i should get wrong here ,cause java don't help me try to parse Stirng mail address to a MailAddress object.
   }
}


and if  the arg definetion of member function of java have a label:
....
  public Function funcDefinetion(Modifer modifer,String className,Arg[] args )
 {
   ...
 }
....

when i wanne invoke the funcDefinetion(), the  order of args will be no longer need care and  
remember:

funcDefinetion(className:"TestClass",args:new Arg[10] ,modifer:new Modifer());

if i have enough knowledege, i would like make my own changes of the language and submit their patch back to the core development team. haha.

---

### Post by LaRoza on 2007-09-14
> **Compyx said:**
> 
AFAIK, the Linux kernel is written in C, probably GNU-C,


With a little ASM.

---

### Post by yestalk on 2007-09-14
exactly, so i think the ASM is so improtant.

---

### Post by CptPicard on 2007-09-14
Are you sure you're at the point where you need to be concerned about kernel development? :) Just asking...

---

### Post by pmasiar on 2007-09-14
I think that lkml with its brutaly honest "put up or shut up" deals with unprepared wannabes more effectively than our ubuntu forums "let's be nice" approach.

I have nothing against newbies, I do stupid mistakes all the time... but certainly they are drain on time if dealing with them nicely.

---

### Post by yestalk on 2007-09-14
and ,if the function definetion args have a label,

the function could diretly transform to a form (maybe a html from or xml schema) like

----------------------------------------------
functionDefinetion                          |
                                                            |
className:_________                       |
args:_______                                       |
modifier:________                              |
 ___________________________________ |

and the label : className,args,modifier are not  "end user friendly display",so,we sould add extenal infromation:

<dictionaryMapping word="A.functionDefinetion.argsLabel.className">
          <endUserFrendlyName>
                         <cn>Lei Ming</cn>
                          <due>???????</due>
                         <en>Class Name</en>
                           <...><...>
          </endUserFrendlyName>
           <otherPopuseMapping>
                   ....
          </otherpopuseMapping>
</dictionaryMapping>


because the "end user friendly display" is another logic of "friendly",so the extenal info is 
nessisery.....at lest , i don't kown the function behavior,but i can't "friendly" display it. it is
the fullinfo design. function tell what he can do,otherwise,the invoke will failue.(don't includ the automaict Type transforming)


and this so object orentid language is out coming..... with fully self describe

the bash will no longer perfer.... :

system.display.Ls viewType:list <highly depend <TAB> key> haha

could be short if their is no confuseing:

s.d.l vt:l

sy.di.ls viewt 

......

s(system).d(display),l(Ls) vt(viewTpye):l(list)

-------------------------------------------------------------
above is "system view" in a system. which admin or dev and their app useing view.

and for user,the directory shoud be user defined.... most of them don't care "system view".(if the care and have access primit,they can)

 it is better to hide (or no right to access) system than than that "etc,home,opt,mnt........" have at lest 30 year no changed ,and in that way those "view" to be only true in free OS area.

---

### Post by yestalk on 2007-09-14
i means that you guy have more knowlege and executive,could you guys write(develope) a javavm kernal directly run on hardware(not as a app runs on other planform) and have the newly language feature?  java language could command or command bundle(scripts),and if the script seem runs well for a long time (abstract ,genally enough.), consider complie it  to let it more fast.........haha .

        i can't write this ,because i just even don't know linux yet.

---

### Post by aks44 on 2007-09-14
> **pmasiar said:**
> I think that lkml with its brutaly honest "put up or shut up" deals with unprepared wannabes more effectively than our ubuntu forums "let's be nice" approach.

I have nothing against newbies, I do stupid mistakes all the time... but certainly they are drain on time if dealing with them nicely.

So true. I could have posted the very same comment. :)


Now, isn't it priceless when, after numerous posts and headaches, a newbie all of a sudden gets "enlightened" thanks to your explanations? :D IMHO this alone is well worth dealing with all the clueless mass... (not to mention that most of the clueless are just plain fun ;))

---

### Post by bapoumba on 2007-09-14
Well..

---

### Post by CptPicard on 2007-09-14
> **aks44 said:**
> 
Now, isn't it priceless when, after numerous posts and headaches, a newbie all of a sudden gets "enlightened" thanks to your explanations? :D IMHO this alone is well worth dealing with all the clueless mass...

No it's not, if I have to start by explaining why I am not going to just roll up my sleeves and get on with implementing my own javavm "on top of hardware" so that we (read "I") can then implement some xml javadoc code documentation system, or "Stacks" or whatever.

Some headaches are not worth it. :) I just wish they all just bought Novell already and went on to create their own legacies... hopefully through some experienced programmers who are paid a *lot* to deal with their clueless bosses who are anyway equipped with an übermensch ego...

(Note: I, too, like n00bs who are interested in learning, and I'm hardly all-knowing myself...)

---

### Post by aks44 on 2007-09-14
> **CptPicard said:**
> Some headaches are not worth it.

Then I guess we'll have to disagree. ;) One can only say that a headache *was* not worth it (once it's all over), but certainly not that it *won't* be worth it (while it's still going on).

IMHO even such an off-topic discussion as we're currently having can help someone realize that before attempting to work on huge projects, one needs to get the basics *right*. ;)

---

### Post by pmasiar on 2007-09-14
> **aks44 said:**
> can help someone realize that before attempting to work on huge projects, one needs to get the basics *right*. ;)

I don't see any evidence of this happening in the cases like mentioned by CptPicard. I cannot dig the link now, so you just trust me :-) : **research found** (so it is not just anecdotal evidence)  that lowest skilled quintile routinely overestimates their skill level. Second lowest quintile **underestimated** their skill level (thinking they are the worst). Lowest quintile **has no idea** how unskilled they are, they assess themselves "about average" and don't feel like they need to learn "that much". 

As we found, programmers are "dime a dozen", while "visionaries" are rare. Or in this case, obvious lack of basic English or programming skills, despite couple gentle hints, did not shake OP attitude - not a iota. It is not a troll, but noise degrades conversation exactly same way.

They say "attitude is not a valid substitute for competence"  for a reason, but many "visionaries"  would strongly disagree... :-)  Another of my favorite quotes from this area goes like: "10 years of experience means nothing only to a person without 10 years of experience".

Once I was recruited to small, young, aggressive, rich, and well-positioned company. I think I was one of the oldest developers, and I had audacity to mention that above quote when talking in some pub. Needless to say, I did not worked there for too much longer. :-)

---

### Post by yestalk on 2007-09-14
&#19981;&#22909;&#24847;&#24605;,&#20320;&#20204;&#35828;&#30340;&#33521;&#35821;&#37117;&#22826;&#38590;&#20102;,&#25105;&#23545;&#30528; &#35789;&#20856; &#37117;&#32763;&#35793;&#19981;&#20986;&#26469;.....

&#20320;&#20204;&#20889;&#20102;&#20123; &#19981;&#22815;&#36890;&#29992;&#30340; &#20442;&#35821;(&#27809;&#26377;&#20351;&#29992;&#26631;&#20934;&#35789;&#24211;&#21834;^_^.),&#32473;&#20102;&#25105;&#19981;&#23569;&#25387;&#25240;&#24863;,&#25152;&#20197;&#25105;&#20889;&#28857;&#20799;&#20013;&#25991;,&#35753;&#20320;&#20204;&#20063;&#25387;&#25240;&#19968;&#19979;.

---

### Post by pmasiar on 2007-09-15
> **yestalk said:**
> &#19981;&#22909;&#24847;&#24605;,&#20320;&#20204;&#35828;&#30340;&#33521;&#35821;&#37117;&#22826;&#38590;&#20102;,&#25105;&#23545;&#30528; &#35789;&#20856; &#37117;&#32763;&#35793;&#19981;&#20986;&#26469;.....

&#20320;&#20204;&#20889;&#20102;&#20123; &#19981;&#22815;&#36890;&#29992;&#30340; &#20442;&#35821;(&#27809;&#26377;&#20351;&#29992;&#26631;&#20934;&#35789;&#24211;&#21834;^_^.),&#32473;&#20102;&#25105;&#19981;&#23569;&#25387;&#25240;&#24863;,&#25152;&#20197;&#25105;&#20889;&#28857;&#20799;&#20013;&#25991;,&#35753;&#20320;&#20204;&#20063;&#25387;&#25240;&#19968;&#19979;.

No, I disagree. But nice characters anyway :-)

You need [ten years to learn programming](http://norvig.com/21-days.html) - read article how.

---

### Post by CptPicard on 2007-09-15
Babelfish:

> 
Embarrassed, you said English too has been all difficult, I treat the dictionary all not to be able to translate You wrote an insufficiently general slang (not to use standard word storehouse ^_^.) For my many setbacks feeling, therefore I write a Chinese, lets your also setback


---

### Post by yestalk on 2007-09-15
the "standard word storehouse" should be translated to "standard library"

"Embarrassed" should be translated to "excuse me"

you use the somewhate goolge like tanslate engine  won't you? 

do you care that if you really understand something in the world or it just integrality in your theory or mind, can't understand the combination of Chinese,so you use some engine  help you. 

i wonder what should be occur out which the engine you use  if i used "&#20013;&#22269;&#35805;" instead of "&#20013;&#25991;" .

we are talking about programm language isn't it? ----------so no doubt the programm language is some kind of language which for human use purpose,won't use the tanslate engine could you feel frustration a litte?

respect the language we use for, respect the job which we liveing on.... i understand a little what you guys  chagrin for. but the c follow the b,however jump to j(java) suddenly(from the view angle of me),then someone think that sould get the c a # to emphasize it..................they just done, i just won't done yet. does these things cranky?

---

### Post by Lord Illidan on 2007-09-15
Personally, I cannot fathom a word of what you're saying. Can you type normally? If not, please excuse me, but I do find it hard to understand.

---

### Post by yestalk on 2007-09-15
if you talking about that the syntax(grammar) which i had wirte,i'm sorry, that is the better i can do present.

if you talking about the Chinese character whiich  i type, that your computer just don't have Chinese character font,or your browser  use  a encoding which is not utf-8.

---

### Post by aks44 on 2007-09-15
> **Lord Illidan said:**
> Personally, I cannot fathom a word of what you're saying.

I'd like to see you writing in chinese... then I guess *he* in turn wouldn't understand a single word of yours.



**@yestalk:**
I can understand your frustration, it's quite hard learning a language that is so different from your mother tongue (I'm learning cantonese, and I'm quite bad at it, so I know the feeling ;)).

The language problem is true for anything related to programming... you can learn the basics using only your own language, but to learn more you *need* to know English, just because 90% of the information available is in English.

Now, here is the problem as I understand it:
- you want to help Ubuntu and Linux development
- to do that, you need to collaborate with other people all over the world
- all international collaboration is done in English (like it or not, that's a fact)
- you are not yet fluent in English, so you can hardly collaborate with other developpers


If you are really interested in programming, don't let that bother you...
Be it English or programming or anything else, as pmasiar said, one needs about 10 years of sustained practice to get a decent level in any area.
Just do it step by step, start with the beginning, that's the only way to do it right. If you are patient and determined enough you will succeed. :)

&#26202;&#19978;&#22909;&#12290;

---

### Post by CptPicard on 2007-09-15
> **yestalk said:**
> the "standard word storehouse" should be translated to "standard library"... "Embarrassed" should be translated to "excuse me"
 

Close enough. I was actually totally surprised Babelfish managed as well as it did. :)

> you use the somewhate goolge like tanslate engine  won't you? 

Yeah, it's pretty handy whenever I come across with a language I don't manage, although I am capable of reading four other languages in addition to my mother tongue (Finnish)...

> do you care that if you really understand something in the world or it just integrality in your theory or mind, can't understand the combination of Chinese,so you use some engine  help you. 

Why not :) if it works, make use of it.

And yes, I care deeply about integrality in my theory and mind. Confucius says, "care for the integrality of your theory or your mind is blown up by n00bs" :(

> i wonder what should be occur out which the engine you use  if i used "&#20013;&#22269;&#35805;" instead of "&#20013;&#25991;" .

It manages it quite well! In simplified Chinese it translates both as "Chinese", although I suspect the former is traditional Chinese, at which point it translates it as "Center.. <square character>". My educated guess is the latter word is or refers to "Kingdom" as "Center/Middle Kingdom" is what China is called locally, no? :)

Anyway, the point was not to get hung up on English. I remotely got the idea of what you were trying to say regarding some kind of semantic additions to some APIs... we already have documentation systems, and adding such semantic assertions would be a huge project, and I'm not really sure even if it's doable.

And most certainly you wouldn't go about it by .. uh, rewriting the Java VM to be more closely integrated to the hardware. You're welcome to go about such a project yourself, but frankly, I feel most of it was nonsense, as much as I was able to get the point (not really that much because of lack of English, but lack of.. point) :)

---

### Post by yestalk on 2007-09-15
ok, i just know its not doable by now , 
 
if it is easy to add new syntax feature, do it ,or don't.

but as my skill level, i don't know where is the hardest point to add and modify syntax feature in a language. for java and c ,c++ they considering compatible of early client code.
so they don't change API and syntax feature liberty.

and for commercial consideration , they "do more with less" -----so programmer do the more...... and so many techbook published ....

but if i know some compiler theory,do some cool things is interesting.just do some modify base on java syntax,if it is real convenience,nobody refuse convenience.

for example: as i called "automatic Type convert" maybe just a compiler time trick to help programmer reduce labor intension(if some code invoke a method with wrong type at runtime ,may occur Exception), or let business logic more centralizely for human readabale and let detail later define;code  reuseable(the convert code ,the significative convertion from one Type to another) etc.

so many IDE could reduce labor intension,but if the syntax no change,it's hard to location the core logic which a function represent for,some thing like see utiler any where.....

as you say ,i well improve my English hardly,and reduce some of my phantasy of such language,but i always attention this area which is someone do cool thing,some language with no conservative commercial consideration.no back compatible ----once modify or remove or add one API, all client code should be rewrite useing new concept of system or design.(i think it good for design concept promulgate and problem feedback) this kind of software should be very slightly size.

---

### Post by yestalk on 2007-09-17
> care for the integrality of your theory or your mind is blown up by

i just don't know Confucius speaks English ,haha, exactly ,the meaning of translated ana of  "&#23380;&#23376;" then retranslate to Chinese does not like identical equation , i believe that there is some information lost. so i can't understand want it exactly mean.

but i know some Confucius words, permit me to let it display in Chinese :"&#30693;&#20043;&#20026;&#30693;&#20043;,&#19981;&#30693;&#20026;&#19981;&#30693;,&#26159;&#20026;&#30693;&#32773;&#20063;" ------"have the wisdom  which know what oneself could handle,and the ability which known what oneself don't know, this kind of people could be the one which really understand the world."

---

### Post by yestalk on 2007-09-17
and aks44, why don't you chose mandarin rather than Cantonese?

---

### Post by aks44 on 2007-09-17
> **yestalk said:**
> and aks44, why don't you chose mandarin rather than Cantonese?

Because I may move to GuangDong soon (very near to Hong Kong if possible, as I'll need to go there frequently). I have the opportunity of creating a business there, it will probably be ready in a year.

---

### Post by eekwong on 2007-09-17
Basically, I am currently on the same boat like yestalk.

I use Java at work, a little Perl, just know very little C, no Python. (like yestalk's situation)

However, I think I started to be interested in Linux that I "wish", one day, I could help a bit on bugs, development or even drivers in the linux world.

Therefore, since the past weekend, I have been reading the famous C book "The C Programming Language 2ed" to try picking up the C back to beginner level at least ;).

Then, I have no idea where to go next, Linux kernel books? pick a project to participate? more C? or is it just too native to even think about those .... or is it too early to think those, try translate some documentation to show your enthusiasm first!?

================================

@yestalk
You need to have more correct grammars in your sentences, what you wrote was directly translated from Chinese and lack of organization. My mother language is also chinese &#20013;&#25991;, and I know Cantonese and Mandarin :)

for example, this sentence:
> if you talking about that the syntax(grammar) which i had wirte,i'm sorry, that is the better i can do present.

if you are talking about the grammar problems in my sentences, I am sorry since that's the best I can do currently. 

(I know my English sucks too, eheh)

---

