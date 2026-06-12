---
title: "Android: Displaying content?"
date: 2011-10-28
forum: Programming Talk
---

### Post by fallenshadow on 2011-10-28
If I want to display content like alot of Strings what would be the recommended method?

1. An array that exports to a text file and imports the data back in.

2. A database of some sort.

---

### Post by 11jmb on 2011-10-28
When you say "a lot" please be a bit more specific. Both of those choices are feasible but require different amounts of work. A database would be better if you need to perform operations like searching etc. but if you are just storing and reading sequentially, a text file might be easier.

Also, how would you like to display these strings? in a table? a scrolling list?

---

### Post by fallenshadow on 2011-10-28
I won't need to search the data... so maybe an array or variables would be good and then store to a text file. Im not sure yet how I want to display the data... I suppose a table would be good or whatever is easiest. :)

---

### Post by 11jmb on 2011-10-28
Do you mind if I ask what you intend to do with this app?

Is saving the text for the future necessary, or are you just concerned with memory usage? 

What kind of text is it? In what form would it look most natural?

---

### Post by fallenshadow on 2011-10-31
Im developing this app just for learning Android development. It won't serve any purpose but I really want to know how to store data and restore it like in desktop apps.

The text will be strings and numbers parsed to strings.. not sure what would suit it best.

However Im having another problem.. ive been trying to get a Linearview to be scrollable but the emulator force closes the app when it loads the activity.

Anything wrong with this?:

> <?xml version="1.0" encoding="utf-8"?>
<ScrollView ...>

<LinearLayout ...>

...
...

</LinearLayout>

</ScrollView>



---

### Post by 11jmb on 2011-10-31
That layout looks ok to me. is there anything else in the program that could be making it crash?

As far as reading and writing text to/from the SD card you should try something like the following:

Reading:
```

File sd_dir = Environment.getExternalStorageDirectory();

File input = new File(sd_dir,"input.txt");

String text = "";

try {
    BufferedReader reader = new BufferedReader(new FileReader(input));
    String line_in;

    while ((line_in = reader.readLine()) != null) {
        text = text + line_in + "\n";
    }
}
catch (IOException e) {
    
}

//add text to your TextView

```

Writing will follow the same general pattern, but will use a FileOutputStream class

---

### Post by fallenshadow on 2011-11-02
Fixed the crashing! :)

Thanks for that code, awesome!

Having major trouble trying to use spinners though. (comboboxes) I copied example code from a book and it doesn't work! :D

Do you know how to use them? or know of an example online?

---

### Post by 11jmb on 2011-11-02
What exactly isn't working with the spinner?

The use described on the android tutorials always worked for me.

[http://developer.android.com/resources/tutorials/views/hello-spinner.html](http://developer.android.com/resources/tutorials/views/hello-spinner.html)

---

### Post by fallenshadow on 2011-11-02
Thanks! I had trouble putting items into the spinner, I guess maybe I was working with a bad example or something. Official documentation is best! :)

---

### Post by fallenshadow on 2011-11-16
Another question... how does one setup onclicklisteners for alertdialogs?? 

I have an alertdialog using a CharSequence and I want to setup actions for each option however I can't seem to figure it out.

---

### Post by 11jmb on 2011-11-17
I'm going to point you back to the official documentation.

[http://developer.android.com/guide/topics/ui/dialogs.html](http://developer.android.com/guide/topics/ui/dialogs.html)

EDITED: Just looked through some of my old code, the methods described in the documentation still work. Sorry if that misled you.

---

### Post by fallenshadow on 2011-11-17
Ah I figured it out now... im having another problem though.

All I want to do is pass an int to another activity but nothing on the internet works.

At the moment I have:

Sending the value:
[PHP]
int myVariable = 1;
				
Bundle b=new Bundle();
b.putInt("key", myVariable);
					 
Intent intent = new Intent(FirstActivity.this,SecondActivity.class);
intent.putExtras(b);
startActivity(intent);
[/PHP]

Receiving the value:
[PHP]
Bundle b=this.getIntent().getExtras();
int s=b.getInt("Key");
[/PHP]

Any ideas as to why this doesn't work?

---

### Post by 11jmb on 2011-11-17
Is it because "key" is capitalized in activity 2? Thats the only problem I can see with what you showed me.

---

### Post by fallenshadow on 2011-11-17
I fixed that but it still force closes when I test the code. :lolflag:

---

### Post by 11jmb on 2011-11-17
I don't think there is anything else wrong with what you posted. Can you post more code? It may be choking on something else.

---

### Post by fallenshadow on 2011-11-19
Here you go:

[link-removed]

Its very small so far... just the beginning of something.

I recommend opening with Eclipse setup with Android if you want to test it.

---

### Post by fallenshadow on 2011-11-21
Can someone show me an example of variable passing?

---

### Post by 11jmb on 2011-11-21
You are on the right track using bundles to pass between activities, and from looking at your code, it looks like you are using them correctly. Are you sure that your program is choking on the bundle?

In other words, try commenting out the bundle calls and just put a Toast.makeText in the GameActivity onCreate to make sure that everything else is working. I can't see anything wrong from looking, but I don't want to debug your code for you.

I do recommend using LogCat, though, if you are not already. It is very helpful for debugging. You can set some breakpoints and step through the code while looking at logcat for warning/error messages

---

### Post by fallenshadow on 2011-11-21
Hmm... even a really, really simple app to switch activity force closes on me. Tested it on Win7 and Ubuntu... something very strange is going on. :confused:

---

### Post by 11jmb on 2011-11-21
That should not be a problem with your operating system. The answer may be very obvious to you by looking at logcat error messages

---

### Post by fallenshadow on 2011-11-22
Silly me, I forgot to edit the android manifest file! The code for variable switching now works! :lolflag:

---

