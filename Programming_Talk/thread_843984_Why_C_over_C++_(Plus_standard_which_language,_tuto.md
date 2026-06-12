---
title: "Why C over C++? (Plus standard which language, tutorial)"
date: 2008-06-29
forum: Programming Talk
---

### Post by DeathOnJuice on 2008-06-29
I've been interested in programming for a while, but was too lazy to do much on my own time up to now. Last year, I took a computer science course at a fairly prestigious high school. It was ridiculously easy. So, if the course was any good, I have a good grasp on Java basics. I really want something to do this summer, however, so I'm mustering my initiative to learn a new language.

I see many recommendations that, if one already knows a language, one should learn C. Why this over C++? I'm also considering Python, but I think it would be better to do a lower level language after Java.

Enough background and musing to myself. Really, this boils down to: Which language should I learn with a year's background in Java? And could I get a tutorial recommended? There are very many in the sticky for each language, and I'd like to get one that's suggested over the others (I'm OCD that way).

As far as books go, I have K+R The C Programming Language 2nd ed and Learning Python (but only 2nd edition - Python 2.3). I have heard good things about The C++ Programming Language by Stroustrup and would not mind buying it if online tutorials are insufficient.

Thanks.

---

### Post by pmasiar on 2008-06-29
If you want to learn closer how hardware works, learn C (C++ is too abstract and too close to Java).

If you want to learn tool which lets you complete tasks (like parsing/manipulating files, creating database or web apps, and other tasks where you prefer flexibility over number crunching speed) 10 times faster than Java (and expand your mind beyond cage of static typing), learn Python.

If you want to learn language what is as close to hardware as C, and can be expanded more and faster than dynamically typed OO language like Python, learn Forth.

---

### Post by DeathOnJuice on 2008-06-29
So, sounds like C++ is really not a good idea. Obviously better than Java (no one likes Java), but I guess I'll do a joint C and Python venture, mayhaps.

Online tutorial recommendations? Or, if anyone does not agree and would like to lend themself to C++, go ahead.

---

### Post by LaRoza on 2008-06-29
> **DeathOnJuice said:**
> So, sounds like C++ is really not a good idea. Obviously better than Java (no one likes Java), but I guess I'll do a joint C and Python venture, mayhaps.

Online tutorial recommendations? Or, if anyone does not agree and would like to lend themself to C++, go ahead.

There is a lot of bias against C++ and Java on this forum, because they are not that fun to work with (incidently, you can get a lot of jobs using them. Makes you wonder...)

Linux and many GNU projects are in C, and Ubuntu recommends Python.

In the end, you choose what you want to learn. I started with C++, and wish I hadn't (I never use C++ now...)

Check out my wiki and my site.

---

### Post by LoneWolfJack on 2008-06-29
A plussie for C++ would be the availability of Qt. But then again, C has GTK (even though that is available for C++ as well).

I'd still go with C. There are no good tutorial sites out there that I know of, but the great thing about C is that you can achieve so much with so few commands (and with so many lines of code, respectively).

The only tricky thing about C for beginners are pointers. But once you get the idea, you'll love them.

---

### Post by DeathOnJuice on 2008-06-29
> **LaRoza said:**
> There is a lot of bias against C++ and Java on this forum, because they are not that fun to work with (incidently, you can get a lot of jobs using them. Makes you wonder...)

Linux and many GNU projects are in C, and Ubuntu recommends Python.

In the end, you choose what you want to learn. I started with C++, and wish I hadn't (I never use C++ now...)

Check out my wiki and my site.

Your site was one of the main reasons I began to question C++. On the small survey to find which programming language one might like, it was not even listed.

Well, I'll get started on C with some Python on the side.

---

### Post by LaRoza on 2008-06-29
> **DeathOnJuice said:**
> Your site was one of the main reasons I began to question C++. On the small survey to find which programming language one might like, it was not even listed.

Well, I'll get started on C with some Python on the side.

That is good. To be fair, I see no situation where I would say "C++ would be perfect for that!". I would be more likely to think "C is what you want" or "Python would be good for that", and for tasks many might choose C++, I would say "Python could do most of that, but you could use C for the tricky bits".

The language selector will never list C++ first, because of this (I programmed it, and gave it *my* logic as best I could)

---

### Post by pmasiar on 2008-06-29
see sticky FAQ for C, wiki in my sig for Python links (is also in FAQ)

---

### Post by pmasiar on 2008-06-29
> **DeathOnJuice said:**
> So, sounds like C++ is really not a good idea. Obviously better than Java (no one likes Java)

It's not about liking Java. Java is dependable workhorse, it is just incredibly boring, once you tasted freedom of dynamically typed languages. I use it for work - it's just so verbose and micromanaging. And with huge boring library. 

Java is little (just a little) better than C++ because has managed memory (garbage collection) so may prevent some memory leaks.

C is exciting because you can feel you are close to the metal - and your mistakes can be much bigger disaster faster than in Java. :-) With more power comes more responsibility.

Python is exciting because you can use 10% of code lines to accomplish same effect than in Java, so you can see clearer what your code is doing. And with dynamic typing, you can do cool magic without being real guru.

---

### Post by lisati on 2008-06-29
I don't like C++ as some of its features seem to be "overkill"

```
printf("Hello world\n");
``` makes more sense to me than something like```
cout<<"Hello world\n"<<endln;
``` (even though I haven't used a printing terminal for several years!

---

### Post by LaRoza on 2008-06-29
> **lisati said:**
> 
```
cout<<"Hello world\n"<<endln;
``` 

Technically, it is:

```

std::cout << "Hello world" << std::endl;

```

---

### Post by lisati on 2008-06-29
> **LaRoza said:**
> Technically, it is:

```

std::cout << "Hello world" << std::endl;

```
thanks: I couldn't quite remember the exact syntax.

---

### Post by Phenax on 2008-06-29
> **lisati said:**
> I don't like C++ as some of its features seem to be "overkill"

```
printf("Hello world\n");
``` makes more sense to me than something like```
cout<<"Hello world\n"<<endln;
``` (even though I haven't used a printing terminal for several years!

printf works in C++ too.

---

### Post by LaRoza on 2008-06-29
> **Phenax said:**
> printf works in C++ too.

So does malloc, but then remind us why C++ is being used?

(Pause while I take a screenshot of my bean count)

---

### Post by Phenax on 2008-06-29
> **LaRoza said:**
> So does malloc, but then remind us why C++ is being used?

(Pause while I take a screenshot of my bean count)

Object Orientation, Generic Programming, Templates, Polymorphism, Data Abstraction

Different languages are good for different things and different people.
[quote="Bjarne Stroustup"]
 Several reviewers asked me to compare C++ to other languages. This I have decided against doing. Thereby, I have reaffirmed a long-standing and strongly held view: Language comparisons are rarely meaningful and even less often fair. A good comparison of major programming languages requires more effort than most people are willing to spend, experience in a wide range of application areas, a rigid maintenance of a detached and impartial point of view, and a sense of fairness. I do not have the time, and as the designer of C++, my impartiality would never be fully credible. 

 I also worry about a phenomenon I have repeatedly observed in honest attempts at language comparisons. The authors try hard to be impartial, but are hopelessly biased by focusing on a single application, a single style of programming, or a single culture among programmers. Worse, when one language is significantly better known than others, a subtle shift in perspective occurs: Flaws in the well-known language are deemed minor and simple workarounds are presented, whereas similar flaws in other languages are deemed fundamental. Often, the workarounds commonly used in the less-well-known languages are simply unknown to the people doing the comparison or deemed unsatisfactory because they would be unworkable in the more familiar language. 

 Similarly, information about the well-known language tends to be completely up-to-date, whereas for the less-known language, the authors rely on several-year-old information. For languages that are worth comparing, a comparison of language X as defined three years ago vs. language Y as it appears in the latest experimental implementation is neither fair nor informative. Thus, I restrict my comments about languages other than C++ to [generalities]("http://www.research.att.com/%7Ebs/bs_faq.html#advanced") and to very specific comments.
[/quote]

---

### Post by LaRoza on 2008-06-29
> **Phenax said:**
> Object Orientation, Generic Programming, Templates, Polymorphism, Data Abstraction


Like Python ;)

Without templates, because they are not needed.

---

### Post by JupiterV2 on 2008-06-29
I'm no master/guru...and I've not used every language out there but...there's a couple generic sayings that describe every computer language:

1. Beauty is in the eye of the beholder.

2. Different strokes for different folks.

3. Preserve wildlife, pickle a squirrel.

Clear as mud? Excellent!

All programming languages fulfill a task. C++ is widely used and has plenty of resources available for learning. Is it the best language? No. Is it the worst? Certainly not!

The majority of Ubuntu users are, typically (note: very over-generalized), pro-Python. Do they have good reason to be? Yes, but make sure you take what they say with a grain of salt. Just like in any field, their arguments for and against something will always be skewed in to their side. How else can they defend their reasons for using it?

I started with C++ (once I took programming seriously) and have moved on to C. I've tinkered with Python but before I got too off track I put it aside for future learning. I plan to tackle it next. What I have seen of it is awesome from a productivity standpoint but is it the be-all end-all? Definitely not.

You just need to ask the following:

1. Am I learning to program in order to get a job? If so, what type of job are you looking for then analyze what languages are most in demand for that particular task.

2. Am I learning to program for a hobby? If so, there is no "wrong" choice. The "right" choice, the correct one, is the language you have fun with and enjoy learning.

Hopefully, this made your decision more difficult for you.

Cheers!

---

### Post by pmasiar on 2008-06-29
> **JupiterV2 said:**
> 3. Preserve wildlife, pickle a squirrel.

One thing what is not laughable is status of our environment. Ie are you aware that basis of ocean food pyramid, zoo plankton, is hard hit by increasing acidity of water from increases of CO2? About half of fish species (feeding on zooplankton) is expected to be near extinct in 50 years. Beneficiary of this change: giant jellyfish.

Florida plans to spend billions to save Everglades, even if everyone knows that 100 years from now, ocean will rise 1m and Everglades will be underwater. Same with New Orleans. Out grandchildren would not understand how we could ignored that and do nothing.

> The majority of Ubuntu users are, typically (note: very over-generalized), pro-Python.

You, like many CompSci pro, have slight disgust for a language which 'mere mortals' with no CompSci education can learn and use to solve problems (without needing you). Of course it is also about job security - security of your job. 

These days, most people using computers don't use them to write programs for sale: they use them to solve own problems, whom which programming is only a very little part. And they don't want to explain you all they know about the problem in order to solve it (and you would not want to learn it anyway).

---

### Post by nvteighen on 2008-06-29
> **JupiterV2 said:**
> 
(...)

You just need to ask the following:

1. Am I learning to program in order to get a job? If so, what type of job are you looking for then analyze what languages are most in demand for that particular task.

2. Am I learning to program for a hobby? If so, there is no "wrong" choice. The "right" choice, the correct one, is the language you have fun with and enjoy learning.

A well-balanced comment.

Just an additional note if you want to be a hobbyist: not only choose whatever language fits more to you (of course, do some research on different languages first), but also, when programming, choose tasks you'll enjoy but you are also able to do. The best way to learn is to do things and experiment; use tutorials as references. And, of course, ask questions in these forums!

---

### Post by dwhitney67 on 2008-06-29
> **pmasiar said:**
> One thing what is not laughable is status of our environment. Ie are you aware that basis of ocean food pyramid, zoo plankton, is hard hit by increasing acidity of water from increases of CO2? About half of fish species (feeding on zooplankton) is expected to be near extinct in 50 years. Beneficiary of this change: giant jellyfish.

It's been a very, very long time since I sat in a chemistry class.  Can you please refresh my memory on how CO2, when mixed with H20, becomes an acid?

Just kidding... I already know the answer... it can't happen.  Perhaps you are thinking of another compound released into the atmosphere that contains Sulphur.

---

### Post by nvteighen on 2008-06-29
> **dwhitney67 said:**
> It's been a very, very long time since I sat in a chemistry class.  Can you please refresh my memory on how CO2, when mixed with H20, becomes an acid?

Just kidding... I already know the answer... it can't happen.  Perhaps you are thinking of another compound released into the atmosphere that contains Sulphur.

H_2CO_3 (carbonic acid) damages our environment? We should stop drinking Coke/Pepsi? :)

---

### Post by pmasiar on 2008-06-29
> **dwhitney67 said:**
> It's been a very, very long time since I sat in a chemistry class.  Can you please refresh my memory on how CO2, when mixed with H20, becomes an acid?

Just kidding... I already know the answer... it can't happen.  

[http://en.wikipedia.org/wiki/Acid_rain](http://en.wikipedia.org/wiki/Acid_rain) and [http://en.wikipedia.org/wiki/Ocean_acidification](http://en.wikipedia.org/wiki/Ocean_acidification)

Ignorance does not solve or prevent problems.

---

### Post by robertchahine on 2008-06-29
Like Laroza said, you can begin with C or python.I know a little bit of python, and began learning C.Those two languages are easy, especially python(with python with single line, you can pirnt an output), plus python and C are so powerful.
N.B: Note that when you're installing some applications for ubuntu, a lot of times, you see python packages installed with it

---

### Post by robertchahine on 2008-06-29
Like Laroza said, you can begin with C or python.I know a little bit of python, and began learning C.Those two languages are easy, especially python(with python with single line, you can pirnt an output), plus python and C are so powerful.
N.B: Note that when you're installing some applications for ubuntu, a lot of times, you see python packages installed with it

---

### Post by LaRoza on 2008-06-29
> **pmasiar said:**
> One thing what is not laughable is status of our environment. Ie are you aware that basis of ocean food pyramid, zoo plankton, is hard hit by increasing acidity of water from increases of CO2? About half of fish species (feeding on zooplankton) is expected to be near extinct in 50 years. Beneficiary of this change: giant jellyfish.

Consider that 99% of all species to have ever existed are extinct, adding more isn't all that catastrophic and I think it is sort of offensive to think Humans are all that special. [http://en.wikipedia.org/wiki/Prehistoric_life](http://en.wikipedia.org/wiki/Prehistoric_life)

> 
You, like many CompSci pro, have slight disgust for a language which 'mere mortals' with no CompSci education can learn and use to solve problems (without needing you). Of course it is also about job security - security of your job. 


[http://www.chunder.com/text/ididit.html](http://www.chunder.com/text/ididit.html)

---

### Post by pmasiar on 2008-06-29
> **LaRoza said:**
> Consider that 99% of all species to have ever existed are extinct, adding more isn't all that catastrophic and I think it is sort of offensive to think Humans are all that special. 

I consider humans quite special. "Humans are not so special" POV makes sense only for a borg (lame joke) or for fundamentalist, who welcomes global climate catastrophe as sign of [http://en.wikipedia.org/wiki/Rapture](http://en.wikipedia.org/wiki/Rapture) (not funny at all). And quite off-topic in any way, so let's end it right there.

All this could be avoided if we avoid pickled squirrels :-)

---

### Post by Phenax on 2008-06-29
> **LaRoza said:**
> [http://www.chunder.com/text/ididit.html](http://www.chunder.com/text/ididit.html)

I hope you're using that humorously, as it's been refuted by Bjarne Stroustrup as a hoax.

---

### Post by holiday on 2008-06-29
To write good C code you have to understand the basic mechanics of memory management, addressing, etc that other languages protect you from. 

You can be a great programmer without learning C, but C will teach you about the computer in ways that other languages won't. It's also an unusually elegant  and expressive language.

For a real trip into how computers work, try some assembly language. Now that is fun! It'll take you a day or more to write a file parser that in a currently popular language you could write in twenty minutes, but you will acquire vision.   

If you're trying to get up a web site fast, then C is not your answer. No matter how good you are at C. Just like if you're coding a video driver or a game engine, Java or Python or Griggle are not your answer.

---

### Post by LaRoza on 2008-06-29
> **pmasiar said:**
> I consider humans quite special. "Humans are not so special" POV makes sense only for a borg (lame joke) or for fundamentalist, who welcomes global climate catastrophe as sign of [http://en.wikipedia.org/wiki/Rapture](http://en.wikipedia.org/wiki/Rapture) (not funny at all). And quite off-topic in any way, so let's end it right there.

All this could be avoided if we avoid pickled squirrels :-)

I didn't mean it that way. I meant it is some arrogant of humans to think we have more control over nature. 

I am a firm supporter of protecting and preserving the natural world :-)

> **Phenax said:**
> I hope you're using that humorously, as it's been refuted by Bjarne Stroustrup as a hoax.

Yes, it was supposed to be funny.

---

### Post by CptPicard on 2008-06-29
The good point about global warming and the subsequent ice-free North Pole is that we finally can prove that Santa lives in Finnish Lapland instead of the Pole. I mean, if Santa really was from the North Pole, he and his elves would be swimming by now. So when next Christmas we see Santa again, he can't have come from the Pole unless he's soaking wet and the sled has pontoons. So he's from Lapland. QED.

---

### Post by hessiess on 2008-06-29
Personaly I hate python becouse it lacks a easy to reed structure, relying entiarly upon indenting to define a block. I find languiges using {} or even "if endif" far more logical and easier to reed. Python cannot even cope with a combination of spaces and tabs. I like C++ becouse its Object oriented and only slightly slower than C. Not that I have programmed anything poticulay complicated(yet).

---

### Post by LaRoza on 2008-06-29
> **CptPicard said:**
> The good point about global warming and the subsequent ice-free North Pole is that we finally can prove that Santa lives in Finnish Lapland instead of the Pole. I mean, if Santa really was from the North Pole, he and his elves would be swimming by now. So when next Christmas we see Santa again, he can't have come from the Pole unless he's soaking wet and the sled has pontoons. So he's from Lapland. QED.

Swimming? As if the reindeer would have lost their wings so to speak...

If he is indeed from Finland, it would explain the fat naked guy rolling in the snow last Christmas...

> **hessiess said:**
> Personaly I hate python becouse it lacks a easy to reed structure, relying entiarly upon indenting to define a block. I find languiges using {} or even "if endif" far more logical and easier to reed. Python cannot even cope with a combination of spaces and tabs. I like C++ becouse its Object oriented and only slightly slower than C. Not that I have programmed anything poticulay complicated(yet).

```

def printit(word):
    print word

```

[php]
void printit(char * word){puts(word);}
[/php]

Readability isn't part of the syntax, but structure.

---

### Post by hessiess on 2008-06-29
> **LaRoza said:**
> Swimming? As if the reindeer would have lost their wings so to speak...

If he is indeed from Finland, it would explain the fat naked guy rolling in the snow last Christmas...



```

def printit(word):
    print word

```

[php]
void printit(char * word){puts(word);}
[/php]

Readability isn't part of the syntax, but structure.

say you have a resnably large function like this one out of my game, I know its not as cleen as it could be. at a glance I can instantly tell that everything between { and } is within a block. Without the obvios blocking my eyes tend to wander around the page macking it hard for me to reed the code. From this code you can also see that I tend to deindent comments by one tab, which also helps to stop my eyes from wandering.

[PHP]
int main()

{

	//device = createDevice(video::EDT_OPENGL, core::dimension2d<s32>(1280, 800), 16, false);



	device = createDevice(video::EDT_OPENGL, core::dimension2d<s32>(1000, 625), 32,

		false, true, true, 0);



	driver = device->getVideoDriver();

	smgr   = device->getSceneManager();	

	device->setEventReceiver(&rv);

	

	for(int x=0; x<irr::KEY_KEY_CODES_COUNT; x++)keys[x] = false;

	

// set up camera

	cam = smgr->addCameraSceneNode();

	cam->setPosition(core::vector3df(0,0,-1.4));

	

// run menu

	Tmenu menu;

	int menu_salection = menu.run_menu(keys,device,smgr,driver, cam);

	

// test menu salection

	switch(menu_salection)

	{

		case(1):

// create the background

	bground = TBackground(level, driver, smgr);

	

// will be in player class

	tux = smgr->addCubeSceneNode();

	tux->setMaterialFlag(video::EMF_LIGHTING, false);

	tux->setMaterialType(video::EMT_TRANSPARENT_ALPHA_CHANNEL_REF);

	tux->setPosition(core::vector3df(1,1.5,-0.00001));

	tux->setScale(core::vector3df(0.04,0.04,.0));

	tux->setMaterialTexture( 0, driver -> getTexture("media/Tux/tux_hammer01.tga"));

	

	

	int tileX	= 1;

	float charX = 1;

	u32 frames=0;

	bool keytest = false;

	int frame = 0;

	

	while(device->run())

	{

		core::vector3df old_tux_loc = tux -> getPosition();

		besic_input(tux);

	// colition detection

		tux -> setPosition(bground.colition(tux -> getPosition(), old_tux_loc));

		

	// camera

		cam->setPosition(core::vector3df(tux->getPosition().X,tux->getPosition().Y,-1.4));

		cam->setTarget(core::vector3df(tux->getPosition().X,tux->getPosition().Y,0));

		

		key_col colected_keys = bground.pick_up(tux->getPosition());

		

	// animate on keypress

		//if(keys[KEY_KEY_A] && keytest == false)

		//{

			bground.Animate(device);

			//keytest = true;

			//frame ++;

		//}

		//if(!keys[KEY_KEY_A])

			//keytest = false;

		

		//if(frame > 99)

			//frame = 0;

			

	// character dead

		if(bground.traps(tux->getPosition()))

		{

			device->closeDevice();

		}

			

	// character direction test

		if(keys[KEY_RIGHT])

		{

			tux -> getMaterial(0).getTextureMatrix(0).setTextureScale(-1.0f,1.0f);



		}

		

		if(keys[KEY_LEFT])

		{

			tux -> getMaterial(0).getTextureMatrix(0).setTextureScale(1.0f,1.0f);



		}

		

	// render	

		driver->beginScene(true, true, video::SColor(0,100,100,100));



		smgr->drawAll();



		driver->endScene();

		

		if (++ frames == 20)

		{

			core::stringw str = L"Tux_GBM [";

			str += driver->getName();

			str += L"] FPS: ";

			str += (s32)driver->getFPS();

			str += "__";

			str += bground.findtile(tux->getPosition()).X;



			str += "__";

			str += frame;

			str += "__";			

			str += tux->getPosition().X;

			str += "__";

			str += tux->getPosition().Y+.2;

			str += ")_key_r_";

			str += colected_keys.red;

			str += "_g_";

			str += colected_keys.green;

			str += "_b_";

			str += colected_keys.blue;

			str += "_y_";

			str += colected_keys.yellow;

			str += "_bl_";

			str += colected_keys.black;

			

			if(keys[KEY_ESCAPE])

				device -> closeDevice();



			device->setWindowCaption(str.c_str());

			frames=0;

		}

	

	}

	}

	device->drop();

	return 0;

}[/PHP]

---

### Post by LaRoza on 2008-06-29
> **hessiess said:**
> say you have a resnably large function like this one out of my game, I know its not as cleen as it could be. at a glance I can instantly tell that everything between { and } is within a block. Without the obvios blocking my eyes tend to wander around the page macking it hard for me to reed the code. From this code you can also see that I tend to deindent comments by one tab, which also helps to stop my eyes from wandering.


A large function in a C style syntax is the worst, as you may have to scroll a lot and lose the closing/opening braces. Actually, functions shouldn't be more than a page, so you are doing it wrong ;)

No you't can tell everything between the { and } is a block, you use the indents to tell that. Unindent your code and then tell me the {} make a difference.

---

### Post by hessiess on 2008-06-29
> A large function in a C style syntax is the worst, as you may have to scroll a lot and lose the closing/opening braces. Actually, functions shouldn't be more than a page, so you are doing it wrong
I have alredy said that its not as cleen as it could be. most of the length of that function is old code thats commented out, but i don't want to delete yet.

> No you't can tell everything between the { and } is a block, you use the indents to tell that. Unindent your code and then tell me the {} make a difference.

Yes indenting well adds alot to the redabilaty, but braces help aswell. Its a mixture of the two that mackes it easy to reed. if-endif has the same effect, if you open something, visualy close it.

I am going to agree to disagree.

---

### Post by LaRoza on 2008-06-29
> **hessiess said:**
> 
Yes indenting well adds alot to the redabilaty, but braces help aswell. Its a mixture of the two that mackes it easy to reed. if-endif has the same effect, if you open something, visualy close it.


<offtopic>
It must be hard to program for a dyslexic, I respect your efforts :-)
</offtopic>

It is visually closed, it is moved over...

---

### Post by pmasiar on 2008-06-29
> **hessiess said:**
> Without the obvios blocking my eyes tend to wander around the page macking it hard for me to reed the code. From this code you can also see that I tend to deindent comments by one tab, which also helps to stop my eyes from wandering.


I cannot imagine how hard is to program for a dyslectic person (and I am glad I do not know). Possibly for such a person, having {} helps readability, and IDE for statically typed language is essential, I'll take your word for it. We had before  a blind programmer who complained that whitespace is hard for him.

I accept that people with different cognitive approach may have different needs - and I am glad everyone can have his or her choice of language, and needs of minority do not have to take precedence over convenience for majority.

But these very specific needs are for people way off of normal curve. For most people with SD of normal distribution, relying on whitespace for structure is simple and natural, in my experience.

---

### Post by JupiterV2 on 2008-06-29
> **pmasiar said:**
> One thing what is not laughable is status of our environment. Ie are you aware that basis of ocean food pyramid, zoo plankton, is hard hit by increasing acidity of water from increases of CO2? About half of fish species (feeding on zooplankton) is expected to be near extinct in 50 years. Beneficiary of this change: giant jellyfish.

Florida plans to spend billions to save Everglades, even if everyone knows that 100 years from now, ocean will rise 1m and Everglades will be underwater. Same with New Orleans. Out grandchildren would not understand how we could ignored that and do nothing.


So what does this have to do with squirrels? They're tasty and good with ketchup. It's not like I'm making calamari! That would just be horrible...

> 
You, like many CompSci pro, have slight disgust for a language which 'mere mortals' with no CompSci education can learn and use to solve problems (without needing you). Of course it is also about job security - security of your job. 

These days, most people using computers don't use them to write programs for sale: they use them to solve own problems, whom which programming is only a very little part. And they don't want to explain you all they know about the problem in order to solve it (and you would not want to learn it anyway).

Know what's awesome? I'm honoured you'd call me a ComSci Pro seeing that I'm self-taught novice. 

Besides, I don't think I dissed Python users. Rather, I simply noted that Ubuntu users are predominantly biased towards Python. I mean, snakes are awesome and the language is no different. Silky smooth...writhes beneath your fingertips....mmm....Where was I? Oh yeah! I fully plan on learning Python because better productivity = awesome for me. Seeing Wyrbiral (hope I spelt that correctly) complete a task in 4-5 lines or less that would take 30 or so in C (and the python code would likely run equally as fast, if not faster) is something I want to sink my teeth into.

I'm just saying that a) it's not the end-all be all (and any programmer worth his/her beans would admit that), and b) that there is merit in any language and pushing one over another is sometimes uncalled for.

---

### Post by JupiterV2 on 2008-06-29
> **LaRoza said:**
> <offtopic>
It must be hard to program for a dyslexic, I respect your efforts :-)
</offtopic>

It is visually closed, it is moved over...

You have NO idea. Being dyslexic sucks...it makes everything difficult. I should know, since I am. Stress only makes it worse...

I wasn't diagnosed until I was 17. Once they DID figure it out, you can get special treatment (like taking tests in a non-stress environment) but then you feel like a retard getting special treatment. So I just chose to ace homework and in-class work and fail tests. Its all for the better really. LOL!

---

### Post by hessiess on 2008-06-29
I don't find programming as a concept that complicated, after all all you are rilly doing is adding numbers together. I just find some languages hard to reed.

just to prove that I have used Python, heares a norghts and crosses game I wrote around a year ago. Shoetly after macing this I became interested in 3D, and stopped programming until recently when I tryed out C++.

```
game = []
gameon = 1
d = 1
run = 2
x = 1
player = 1
qd = 1
#### vairables for check
test = 1
reed=[]

def checkreed():
    global test
    global gameon

    test = reed.count('x')
    if test == sise:
        print
        print 'yay! '+player1
        gameon = 0
    test = reed.count('O')
    if test == sise:
        print
        print 'yay!'+player2
        gameon = 0



        
def check():
    global reed
    global mode
    py = 0
    px = 0
    reed = []
    
## check verticly

    for line in game:
        for line in game:
            reed = reed + [game[py][px]]
            py=py+1
            
        checkreed()
        reed = []

        px=px+1
        py = 0
            
    py = 0
    px = 0
    reed = []
    
##  check horosontialy

    for line in game:
        for line in game:
            reed = reed + [game[py][px]]
            px=px+1

        checkreed()
        reed = []

        py=py+1
        px = 0

    py = 0
    px = 0
    reed = []

##  check diagonal 1

    for line in game:
        reed = reed + [game[py][px]]
        py=py+1            
        px=px+1

    checkreed()
    reed = []

    py = 0
    px = 0
    reed = []

##  check diagonal 2
    

    px=sise-1
    for line in game:
        reed = reed + [game[py][px]]
        py=py+1            
        px=px-1

    checkreed()
    reed = []




    




##choose player name
while run > 1:

    
    player1 = raw_input('player 1')
    player2 = raw_input('player 2')

##  choose table sise   
    while x > 0:
        x = 1
        sise = int(raw_input('sise?'))
        if sise < 3:
            print 'to small! _>3'
        elif sise > 20:
            print 'to big!'
        elif sise in range(2,21):
            x = 0
        
## construct gamebord
    for fg in range(0,sise):
        game.append(['?'])
    for x in range(0,sise-1):
        for fh in range(0,sise):
            game[fh] = game[fh]+['?']

##  draw table   
    for line in game:
            print line
            print
## main loop
    while gameon>0:
        if player == 1:
            print player1
        elif player == 2:
            print player2
##      player choose position
            
        while qd in range(1,3):
            placex = input('place x?')-1            
            placey = input('place y?')-1
    ##      check if position is used 

            if game[placey][placex] =='x':
                print
                print 'used!'
            elif game[placey][placex] =='O':
                print
                print 'used!'
            elif game[placey][placex] == '?':
                qd=4
        qd=1
        

        print
##      add  turn to the table  
        if player == 1:
            game[placey][placex] = 'x'

        elif player == 2:
            game[placey][placex] = 'O'

##      test for win      
        check()

##      draw table and switch player
        for line in game:
            print line
            print
        if player == 1:
            player = 2
        elif player == 2:
            player = 1
    game = []
```

---

### Post by pmasiar on 2008-06-29
> **JupiterV2 said:**
> So what does this have to do with squirrels?

It's not about squirrels. You might not care about preserving environment - I am deeply concerned about it.

> there is merit in any language and pushing one over another is sometimes uncalled for.

yes, but if someone not familiar with a language particularly good for some tasks argues against that language (based on not knowing it), should person knowing both, and understanding the difference, remain neutral to pretend be "fair and balanced"? That would be disservice to all interested, IMNSHO.

---

