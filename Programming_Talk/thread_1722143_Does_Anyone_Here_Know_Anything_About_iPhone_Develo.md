---
title: "Does Anyone Here Know Anything About iPhone Development"
date: 2011-04-05
forum: Programming Talk
---

### Post by steveone on 2011-04-05
I'm trying to create an iPhone app and that means I have to use Objective-C. I've been reading as much stuff as I can find, but I'm stuck. I'm trying to use the user's input from a textbox as the key for the object in a dictionary class. If anyone here can help me, it would be greatly appreciated. Thanks.

---

### Post by r-senior on 2011-04-06
You need to be a bit more specific, perhaps post some code or a more detailed description of what you are trying to do?

At a basic level, you need something like this:

```
NSString *key = myTextField.text;
MyObject o = [myDictionary objectForKey:key];

```

I suspect the problem is more than that.

---

### Post by jerome bettis on 2011-04-09
objective C can go @!#$ itself.  It's crap.  Steve Jobs purchased it so he has to run around championing it regardless of how third world it really is.  It's crap to program in. :mad:

---

### Post by simeon87 on 2011-04-09
> **Felipe01 said:**
> [FONT=&quot]IPhone is a great gadget to have, it’s good that you are trying to create an iPhone app on your own. Creating an iPhone app or iPhone development is not an easy thing to do. I think it would be better if you consult or take guidance from professional iPhone developers for better results.      

 
 [/FONT]

I disagree, it can't be that difficult for the average programmer. You just need to learn Objective-C and the platform on which the app will run (e.g., API calls). There's nothing a professional developers knows that we can't learn.

---

### Post by r-senior on 2011-04-10
> **simeon87 said:**
> I disagree, it can't be that difficult for the average programmer. You just need to learn Objective-C and the platform on which the app will run (e.g., API calls). There's nothing a professional developers knows that we can't learn.
+1

A large number of iPhone developers aren't "professional" iOS programmers in the sense that they aren't employed by someone to write iOS apps. Many people write apps for the app store for the challenge and perhaps to make a bit of cash. Some write apps hoping to make a fortune. It's only relatively recently that corporate interest has started to grow, with companies training up their own programmers to write their own apps.

iOS development isn't in itself that difficult. Probably similar in level to writing with Python/GTK and Glade. Anyone who's programmed in C or an OO language like Java/Python would have no trouble picking it up.

---

### Post by Wistful on 2011-04-10
If you have C# (.NET) experience you might like [MonoTouch]("http://monotouch.net/").

> 
What is MonoTouch?

[COLOR=Red]MonoTouch[/COLOR] allows developers to create C# and .NET based applications that run on Apple's iPhone, iPad, and iPod Touch devices, while taking advantage of the iPhone APIs and reusing both code and libraries that have been built for .NET, as well as existing skills

[COLOR=Red]Features[/COLOR]
[LIST]
[*]    Mono for the iPhone, iPad and iPod Touch
[*]    C# and .NET on the iPhone
[*]    .NET Bindings to Native APIs
[*]    Distribute on the Apple App Store
[*]    Enterprise deployable
[*]    MonoDevelop Integration
[/LIST]


[_Documentation_]
[LIST]
[*]A good book&site with some examples: [http://monotouchexamples.com/](http://monotouchexamples.com/) , besides the tutorials and documentation available on the official site. 
[*]And lets not forget the programmers best friend: [http://tinyurl.com/lamxj7](http://tinyurl.com/lamxj7)
[*]For other Mono books see: [http://www.amazon.com/gp/registry/wishlist/ref=gno_listpop_wi](http://www.amazon.com/gp/registry/wishlist/ref=gno_listpop_wi)
[/LIST]

---

### Post by Some Penguin on 2011-04-11
> **simeon87 said:**
> I disagree, it can't be that difficult for the average programmer. You just need to learn Objective-C and the platform on which the app will run (e.g., API calls). There's nothing a professional developers knows that we can't learn.

Speaking as somebody who works with people who *are* involved in professional, decently-funded iPhone app development -- while Objective C isn't that horrible from a programming language theoretic sense, there isn't nearly as much of an functioning ecology of development tools (you've got Xcode, your iFoo simulator, and basically... that's it.  Even for Java, which is considerably younger than C and C++, you've got Eclipse, Netbeans, IntelliJ Idea, and other IDEs; multiple VM implementations; mature build tools like Maven and Ant...) as you do with, say, the C or Java families.  You also don't have <i>nearly</i> the same amount of accumulated man-hours building and testing libraries. 

You're much more heavily dependent on whatever Apple provides, and that doesn't come close to matching the scope of what's available to most general-purpose languages.

---

### Post by steveone on 2011-04-11
> **r-senior said:**
> +1

A large number of iPhone developers aren't "professional" iOS programmers in the sense that they aren't employed by someone to write iOS apps. Many people write apps for the app store for the challenge and perhaps to make a bit of cash. Some write apps hoping to make a fortune. It's only relatively recently that corporate interest has started to grow, with companies training up their own programmers to write their own apps.

iOS development isn't in itself that difficult. Probably similar in level to writing with Python/GTK and Glade. Anyone who's programmed in C or an OO language like Java/Python would have no trouble picking it up.

Hi. Thanks for the reply. I'm relatively new to programming in general. I learned some Java in college and then C#. Prior to having this idea for the iPhone app, I had been learning Python and Python/GTK. I really like Python and I just found out that Android apps are written in Java. I'm looking forward to that. The problem with Objective-C is how difficult it is to find help answering questions, which is why I posted this thread in the first place. It seems it would be easier to show someone what I've done and maybe they would be able to tell me why it's not working the way I expect. For example, this is the code I wrote to get the definition from my dictionary class:

-(IBAction)meaning{
    NSString *word = textField.text;
    NSString *newMeaning = [myDictionary objectForKey:@"%@", word]; 
    meaning.text = newMeaning;

Again if anyone has Skype and has some advice please add me. Skype name steve.one2
Thanks again

---

### Post by steveone on 2011-04-11
> **r-senior said:**
> You need to be a bit more specific, perhaps post some code or a more detailed description of what you are trying to do?

At a basic level, you need something like this:

```
NSString *key = myTextField.text;
MyObject o = [myDictionary objectForKey:key];

```I suspect the problem is more than that.

Thanks for replying.
This is what I have now:

-(IBAction)meaning{
    NSString *word = textField.text;
    NSString *newMeaning = [myDictionary objectForKey:@"%@", word]; 
    meaning.text = newMeaning;

As you can see it's quite similar to what you suggested, but the app crashes when I try to get the meaning of the word. The frustrating thing is that there are no errors to fix. 
Thanks again.

---

### Post by steveone on 2011-04-11
> **Wistful said:**
> If you have C# (.NET) experience you might like [MonoTouch]("http://monotouch.net/").



[_Documentation_]
[LIST]
[*]A good book&site with some examples: [http://monotouchexamples.com/](http://monotouchexamples.com/) , besides the tutorials and documentation available on the official site.
[*]And lets not forget the programmers best friend: [http://tinyurl.com/lamxj7](http://tinyurl.com/lamxj7)
[*]For other Mono books see: [http://www.amazon.com/gp/registry/wishlist/ref=gno_listpop_wi](http://www.amazon.com/gp/registry/wishlist/ref=gno_listpop_wi)
[/LIST]


Thank you for replying. I will definitely look into this. I've created apps using monodevelop and I love it. This way I can go back to working on my Ubuntu machine, which is where I prefer to be. :D
Thanks again.

---

### Post by simeon87 on 2011-04-11
> **Some Penguin said:**
> Speaking as somebody who works with people who *are* involved in professional, decently-funded iPhone app development -- while Objective C isn't that horrible from a programming language theoretic sense, there isn't nearly as much of an functioning ecology of development tools (you've got Xcode, your iFoo simulator, and basically... that's it.  Even for Java, which is considerably younger than C and C++, you've got Eclipse, Netbeans, IntelliJ Idea, and other IDEs; multiple VM implementations; mature build tools like Maven and Ant...) as you do with, say, the C or Java families.  You also don't have <i>nearly</i> the same amount of accumulated man-hours building and testing libraries. 

You're much more heavily dependent on whatever Apple provides, and that doesn't come close to matching the scope of what's available to most general-purpose languages.

So what exactly are you implying? If you have no technical knowledge then it's better left to professionals but anyone with decent technical skills can learn and develop an iPhone app without professional guidance. Given that smartphones simply didn't exist some years ago, we've all had to learn how it works and how to develop apps for it.

---

### Post by r-senior on 2011-04-11
> **steveone said:**
> Thanks for replying.
```
-(IBAction)meaning{
    NSString *word = textField.text;
    NSString *newMeaning = [myDictionary objectForKey:@"%@", word]; 
    meaning.text = newMeaning;
```

I can see what you are trying to do (but I'm not sure why you are trying to do it). Let's sort out your approach first. You are trying to do a sprintf-style string but you are just passing the format string and the substitution parameter. I think you need this:

```

NSString *newMeaning = [myDictionary objectForKey:[NSString stringWithFormat:@"%@", word]]; 

```

I'm not why you are trying to use a format string though. Why not just:

```

NSString *newMeaning = [myDictionary objectForKey:word]; 

```

Or, taking the whole thing and writing more concisely:

```

meaning.text = [myDictionary objectForKey:textField.text];

```

Was there some reason you thought you couldn't do that. Or do you have some addition in mind?

(There is a strong possibility that the dictionary doesn't contain the user-entered field of course, but lets not muddy the waters for the time being).

EDIT: On the subject of debugging crashes, have you set global breakpoints in Xcode so you can see when it bombs out? If not, which Xcode are you using? 3.2 or 4?

---

### Post by steveone on 2011-04-11
> **r-senior said:**
> I can see what you are trying to do (but I'm not sure why you are trying to do it). Let's sort out your approach first. You are trying to do a sprintf-style string but you are just passing the format string and the substitution parameter. I think you need this:

```

meaning.text = [myDictionary objectForKey:textField.text];

```Was there some reason you thought you couldn't do that. Or do you have some addition in mind?

(There is a strong possibility that the dictionary doesn't contain the user-entered field of course, but lets not muddy the waters for the time being).

EDIT: On the subject of debugging crashes, have you set global breakpoints in Xcode so you can see when it bombs out? If not, which Xcode are you using? 3.2 or 4?
Thanks for all your advice r-senior. I am trying your suggestions. I am using version 3.2.6 of Xcode. To be honest, the reason I didn't write it that way is because I didn't know I could. This is why I'm so grateful to people like yourself who have the wisdom of experience to help. I've replace the code I had with 
```

meaning.text = [myDictionary objectForKey:textField.text];

``` I'm getting a warning that 'myDictionary' may not respond to '+objectForKey'. I have a feeling this is the reason the app crashes. I will try to set the global breakpoints to find out for sure. Thanks again.

---

### Post by r-senior on 2011-04-11
If it says it may not respond to a message, that is usually a warning from the compiler that you've declared something as one type and are using another.

Did you remember to declare the dictionary as a pointer (with the '*')? All *objects* in Objective-C are declared as pointers.

---

### Post by steveone on 2011-04-11
> **r-senior said:**
> If it says it may not respond to a message, that is usually a warning from the compiler that you've declared something as one type and are using another.

Did you remember to declare the dictionary as a pointer (with the '*')? All *objects* in Objective-C are declared as pointers.

This is my .h for myDictionary  class
```

@interface myDictionary : NSObject {
    NSMutableDictionary* myDictionary;

}
@property (nonatomic,retain) NSMutableDictionary *myDictionary;
+(id *) myDictionary;

@end

``` I went with (id) because I was getting an error with (void). What do you think? Is this not set correctly?

---

### Post by Some Penguin on 2011-04-11
Not implying anything, I'm simply stating that the universe of tools and libraries is considerably and inevitably smaller, and that the devs I talk with (including somebody who used to develop iOS apps at Apple itself) generally take a fairly dim view of XCode compared to tools for other languages.  As a result, you may find it slower or more obnoxious to get going in.

---

### Post by r-senior on 2011-04-11
> **steveone said:**
> This is my .h for myDictionary  class
```

@interface myDictionary : NSObject {
    NSMutableDictionary* myDictionary;

}
@property (nonatomic,retain) NSMutableDictionary *myDictionary;
+(id *) myDictionary;

@end

``` I went with (id) because I was getting an error with (void). What do you think? Is this not set correctly?
Ah, I think I see your thought process. You want to share this dictionary between view controllers - yes? I struggled with the same thing.

An option for smaller applications is to put the property on the application delegate. So you'd declare myDictionary in the XXXAppDelegate.h file with the @property declaration, then @synthesize in the XXXAppDelegate.m file. (But don't declare an extra class method to access it - you don't need the one that begins with the '+').

Then you can get a reference to the app delegate (which is a singleton class - you always get the same instance), in your view controllers using something like this:

```

XXXAppDelegate *appDelegate = [[UIApplication sharedApplication] delegate];
meaning.text = [appDelegate.myDictionary objectForKey:textField.text];

```

Maybe it's my Java background, but I think this is a pretty shoddy way of doing it. Data doesn't belong on the application delegate IMO. So I'd typically create a singleton class for shared data. I think that's what you are trying to do but haven't quite got it. How about you have a bash with the application delegate to see how it works and I'll dig out an example?

ps. Bear in mind I'm quoting this code off the top of my head at an Ubuntu laptop, not at a Mac, so it might need tweaking.

---

### Post by steveone on 2011-04-11
Thanks r-senior. I'll give that a go. Hopefully I'll have some good news soon. I'd like to see the example if you get a chance.

I think my dictionary may be too big for this solution but I'd like to see what you are thinking.

---

### Post by youbuntu on 2011-04-11
Just wait until you have to start faffing about with all that certificate signing request crap, and development profiles... endless hours of "fun". Not. :?

I bailed out on it, after having torn my hair out for over a year, AND paying £60 for the priveledge! Good old Apple and their square brackets and '@' symbols galore :P

*sigh*

---

