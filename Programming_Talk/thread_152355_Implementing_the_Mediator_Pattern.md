---
title: "Implementing the Mediator Pattern"
date: 2006-03-29
forum: Programming Talk
---

### Post by norfenstein on 2006-03-29
I've been trying to figure out how best to implement the mediator pattern and am having issues deciding how colleagues should communicate with the mediator. This is something almost every resource I've found tends to gloss over and none of the solutions I know of are completely satisfactory. I'm not doing this for anything terribly important so I can afford to fuss over "ideal solutions," but I could really use some perspective from anyone with actual experience.

Here's what I have so far:

To fulfill its role as a filter between colleagues, the mediator has to know what colleagues call it and that means passing a *this* pointer and using an if-statement to make sure the caller matches one of the mediator's colleague references. The problem is that sending only a blank notice to the mediator that a particular colleague has changed is less than ideal; colleagues will not always want to keep around variables to reflect state changes (e.g. there'd be no reason have a a "quit" bool sitting around being false until the very end of a program) and it doesn't seem appropriate for a mediator to care enough about colleague implementations to interpret their internal states anyway. I could use a variadic function, but at that point there's little reason not to just use separate functions for every event. This is the best solution I know of but it requires a one line if-statement at the top of every function to make sure the colleague references being passed to them actually point to one of the mediator's (and it's very tempting to just leave this out since colleagues would need to go out of their way to call a function they shouldn't be).

The example in Design Patterns uses a single entry point mediator with colleagues that only do one thing each. Maybe I shouldn't design colleagues that do more than one thing, but my impression was that an ideal mediator would have one function for every event, callable only by appropriate colleagues, that do nothing but call identically named functions in the colleagues that need notification. In C++ at least there doesn't appear to be a perfect way to do this. Should I stop looking for a perfect solution or is there something I haven't considered? I'd rather not change languages, but as a point of interest is there another language that can do this significantly better?

---

### Post by LordHunter317 on 2006-03-29
> **norfenstein]I've been trying to figure out how best to implement the mediator pattern[/quote]Why?  My opinion of the mediator pattern is that unless you have a situation where you have multiple types of inputs yielding the states and multiple recievers or output states (i.e., a multiplixer or a logic chooser), you don't need one.

IOW, let's say you have some input that needs that has to be treated differently in multiple ways.  A quick example in a GUI would be 'File -> Quit', the window 'Close' button, and a 'Quit' button in your GUI proper.  All three require the same response, but are different inputs and may need to be responded to differently.

Now, regardless of who responds to this input, an action needs to be performed.  This action that needs to be performed varies depends on some state and requires calling different methods depending on it.  Multiple people want to know it's time to quit, too.

Continuing our example, you may need to save first before quiting, or prompt the user, or do one of several other things.  What actions need to be taken are independent of *who* called the mediator.  What outputs are taken are also independent of *who* called it.  

If you don't have that scenario, you shouldn't use such a pattern.  It isn't helping you.  

More succintly: if you cannot make your decision on what actions to take solely based on the state change (and not who made it) then you don't have a valid situation for a mediator pattern.  Period.

Mediators cannot be used to decouple dependencies that strongly exist, and any attempt to do so just adds complexity for no gain.

IOW, if when the windows close button is clicked and only when it is clicked, you need to perform some special action, the mediator isn't responsible for that.  Handle it directly.  The other actions could still be handled by the mediator.

> and am having issues deciding how colleagues should communicate with the mediator.Events are almost universally prefered.  Whether the mediator defines the events and the clients register as senders or whether the clients define the events and the mediator defines a listener is up to you.

Simple would be to have a 'SendEvent()' method on the mediator.  It takes some interface 'Event' and the clients pass it a subclass of that interface.  Obviously, more specific methods for type safety may be required.

> This is something almost every resource I've found tends to gloss over and none of the solutions I know of are completely satisfactory.this is because the mediator pattern tends to be applied incorrectly universally.  The scenarios it's valid for are frequently as easily handled in other ways, and don't occur often naturally.

And when they do occur, systems like expert-rule systems work just as well if not better.

> To fulfill its role as a filter between colleagues, the mediator has to know what colleagues call it and that means passing a *this* pointer and using an if-statement to make sure the caller matches one of the mediator's colleague references.If for some reason you want to ensure only registered collegues can perform mediation (not sure that's an out-and-out requirement) then just store a list of them.  If necessary, make them implement IMediator or similar interface.  If not, then just store a void* and don't care about type.

> The problem is that sending only a blank notice to the mediator that a particular colleague has changed is less than ideal said:**
> If another colleague needs to know about colleague registration, changes are you don't have a mediator pattern.  The colleagues shouldn't have to know anything about each other.

In any case, this is also easy: the mediator exposes events that colleagues can choose to listen to if they wish.

[quote]and it doesn't seem appropriate for a mediator to care enough about colleague implementations to interpret their internal states anyway.Correct.  If you cannot define and function only on "external" states, you cannot apply this pattern.

[quote]I could use a variadic function,I fail to see what htis gives you.

> but at that point there's little reason not to just use separate functions for every event.For each external state?  It's that or inheritance or maybe a template (but that won't yield gains here).

> Maybe I shouldn't design colleagues that do more than one thing, but my impression was that an ideal mediator would have one function for every event, callable only by appropriate colleagues, that do nothing but call identically named functions in the colleagues that need notification.Essentially, yes.  

>  In C++ at least there doesn't appear to be a perfect way to do this. Yes, there is.  Define everything as specifically as you can.  If you can inherit, great.  If you can't, that doesn't make anything wrong.

IOW, let's say you define a mediator for your entire application.  You may have a startup event that's unique, a quit event that's unique, and a file open event that's unique.  Multiple sources can cause all of these and multiple objects want to here.  In which case, some skeleton such as:```
struct IMediator {
    virtual void addStartupSender(void* sender) = 0;
    virtual void addStartupListener(const IStartupEventListener* listener) = 0;
    virtual void doStartup(void* sender, const IStartupEvent& event) = 0;

    // Same three functions for quit, etc, with interfaces varied as appropriate.
}
```That's one way, but rather monolithic.  From this design, a slightly smarter one becomes apparent:```

struct IMediator {
    virtual void addSender(void *sender) = 0;
    virtual void addListener(const T* listener) = 0;
    virtual void sendEvent(const U& event) = 0;
}
```One can then create three classes for each mediator: the mediator, QuitMediator or QuitMultiplexer; the listener T, IQuitListener (likely a single method); and the event U, IQuitEvent.  This is less monolithic then a single class and is really just more scaffolding.  Boost's signals and slots libraries might be able to help here, as well.  Depening on the implementation details, you likely can make a single generic mediator that uses templates for the events, provided you can provide a single listener interface for all listeners.  I can provide a demo if you want, but it requires substantially more explanation.

If you don't need to keep track of legal senders, then the complexity goes down quit a bit: you only need to keep a list of listeners, not both.  Very likely, you don't care about who sends the event, only who gets it.

---

### Post by norfenstein on 2006-03-30
Thank you for such a detailed reply. I think I didn't explain some things very well, but you seem to know know enough about the subject for two of us.

If I understand correctly, you're saying that the mediator pattern should only be used when it doesn't matter where an event comes from. My intention was to use this pattern for a modest but reusable game engine with colleagues like MainLoop and Input. In this situation the program would still function if a colleague generated a strange event (Audio generating a Quit event for example), but it bothers me for the same reason global functions do.

That was my whole problem really, and I could solve it by checking where each event comes from, but I wondered if there was a more elegant solution. Your method has given me something to think about (it hadn't occurred to me use more than one mediator for different events) but it doesn't look like it'd get me out of having to do manual verification. It is clear now that it'd be better to find an approach that doesn't require this.

Thanks again for your time.

---

### Post by LordHunter317 on 2006-03-30
[QUOTE=norfenstein]If I understand correctly, you're saying that the mediator pattern should only be used when it doesn't matter where an event comes from.[/quote]Rather, I'm saying the outputs shouldn't care where the event came from.  IF they care, it's a strong dependency between that input and output.  Mediator only adds complexity here.

> That was my whole problem really, and I could solve it by checking where each event comes from, but I wondered if there was a more elegant solution.My whole point is that if you have to be doing these checks, you may be attempting to fit a square peg in a round hole.

---

### Post by j.bean on 2007-11-12
You may consider the option to use an observer pattern for communication.

see 
[http://www.oodesign.com/oo_design_patterns/behavioral_patterns/mediator_pattern.html]("http://www.oodesign.com/oo_design_patterns/behavioral_patterns/mediator_pattern.html")

---

### Post by Kadrus on 2007-11-12
Wow...this thread has been going for about a long time!

---

### Post by hod139 on 2007-11-12
Odd to revive such an old thread.  I miss LordHunter317; he had a way of keeping people honest and making things interesting around here.

---

