---
title: "MVC, MVVM, MVVMC - Questions"
date: 2015-08-29
forum: Programming Talk
---

### Post by slooksterpsv on 2015-08-29
Hello All,

I do C# development and I have a few questions about how you guys feel you should split Models, View Models, Controllers, and Handlers.

Currently, I'm working on an application using MVVM and for the test cases I'm using NUnit. I'm wondering how do I tell what should be in a controller, what should be considered a handler, and when to split this data? I'm thinking I want most of the logic that doesn't deal directly with the display of the data to be in a controller or handler. For example:

If I have a ListBox with 20 items in it; when I load those, I want the controller to process all of that. The View should display the data and the Model should describe it.

What do you guys think? What would be the appropriate way to do this?

---

