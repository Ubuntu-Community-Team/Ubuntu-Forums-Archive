---
title: "Need help designing/planning out layout editor for website."
date: 2009-04-05
forum: Programming Talk
---

### Post by hockey97 on 2009-04-05
Hi, I am currently trying to make a layout editor for my website for ussers to customize their layout and save it.

I plan on having 2 layouts per person. I plan to use the Time as a input to determine which layout to pick.

I want a daytime layout and a night time layout.

So if a client is looking at my layout at 12:00am I should have a night time layout look.

So now I have to figure out how I am going to go abouts doing this. I want to do this right and painlessly as possible.

I thought can't I store 2 css styles in mysql. I think that was my first option I thought of and still think it's the best way to do it.

Then I thought why not store it in a css file in the users folder on my server.

I thought about it but thought it required more coding and also will take long to do such a thing. The reason is that I would have to use code to open the file find each value if it's possible I don't think it is.

Then I wondered if I can do it with python. Now sure about this.

So all I know is I plan to use javascript to create a user interface.

Where they can drag and drop elements onto the layout. Once they like the layout they then can click a button to save it.

So the javascript could grab every elements css position and height and width values.

It would be stored in the mysql database for the user. 

I also thought about how I can generate the html code. So the users can delete and add elements onto the layout.

I thought the best way was to store it in mysql. Then I can load what's stored into the profile layout page which is their profile page.

So I ask here what's the best way to do such a thing. 

Should I store css and html in mysql. If so then how would I go abouts doingit.

Should I make a table and each row would hold values  not css code.

I then have the profile page in php where it will hold the css code and then load in those values from mysql into the variable parts of the css code.

So I am just asking what's the best way to do such a thing? 

Should I store html and css in mysql.  Or store it in  a file and save it in the users folder on my server?

Or just use python and make the editor as a web app?

I am not experienced with using python to make web applications.

I would like to hear your thoughts.

I want to do this as painless as possible meaning less code and finish this as quick as possible without losing any quality of the editor code.

Thanks for your tiem.

---

