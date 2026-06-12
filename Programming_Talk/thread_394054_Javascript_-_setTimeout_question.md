---
title: "Javascript - setTimeout question"
date: 2007-03-26
forum: Programming Talk
---

### Post by ironfistchamp on 2007-03-26
Hey all you web-wizards,

I've got me a little question here. I have a script that uses an external PHP file to get data from a MySQL table and then update what is on the page. You know AJAX stylee, or near enough. Anyway my issue is this. I want this script to run again every 20 seconds (only for testing purposes it will be every minute when its live, maybe longer). The only way I seem to be able to do this is with setTimeout at the end of the function and then make it call itself. I am just wondering if this is not going to be a bad thing as I assume that the original call of the function will never finish, unless it does the timeout thing, calls the function and ends itself while the new call does what it is doing.

Does anyone have any feedback on this or am I talking out of my a***? 

Thanks

Ironfistchamp

---

### Post by Tomosaur on 2007-03-26
You should try and avoid making functions call themselves if you intend the recursion to be infinite - or until the user closes the browser.

When one function calls another, the first function ceases execution until the second function terminates. However, the position at which the second function is called is stored in memory, so that the interpretor knows where to revert to once the second function is complete. The same thing happens when a function calls itself. The first function cannot 'end itself' while a different function is executing (unless you use multiple threads, which - as far as I'm aware) is curently impossible in JavaScript). This is exploited in virtually every program you are likely to come across. In games it is commonly referred to as the 'main game loop' or something of that nature. The idea is that **while** some condition or state is true, some function is called repeatedly. The condition is usually set to false when the user clicks the 'exit' button or otherwise wishes to end the program.

The reason it is bad for functions to self-call is that the client may end up using lots of memory to keep track of its call list. This may NOT happen, but it depends on the specific implementation of the interpretor - and since you don't know this, it's best just to avoid it all together. The following psuedo-code is much more appropriate than self calling:
```

function main(){
  while(true){
    wait(20000);
    updater_function();
  }
}

function updater_function(){
  //code to update page here
}

```

Using the above method - you do not store up a massive call-list (even though it's unlikely to be a big concern, it's just better to avoid getting into the habit). Instead - your program continuously checks whether 'true' is true (which, obviously, it is), then waits for 20 seconds before calling the updater function. Once the update function is finished executing, the interpretor again checks whether true is true, etc etc.

One thing you may want to consider is that if you're updating the whole page, it is unnecessary to enter into a loop - you can just say 'wait 20 seconds and then refresh the page'. The javascript will be reloaded once the page is refreshed anyway. You should only enter into the loop if you're updating only one bit of your page, such as an iframe, because only then is the javascript kept in memory and thus continuously running.

---

### Post by ironfistchamp on 2007-03-26
Genius! Thanks. Don't know why I didn't think of that it makes sense. 

That is exactly what I need as I am only updating a small section of the site. This will keep things working well.

Thanks again

Ironfistchamp

---

