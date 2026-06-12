---
title: "PHP GLobal Variables, Bad?"
date: 2008-03-31
forum: Programming Talk
---

### Post by The Titan on 2008-03-31
I have been reading around on some google searches because a frien dof mine told me that global variables should NEVER be used... He said they are dangerous to your script especially if your globaling(word?) a class.  I read that this is because that means they can be changed, but isn't that the point?  To bring a variable from the global scope to the local scope to modify/access it?  What is SO horrific about using a global variable? And is there a general workaround for this?

---

### Post by rye_ on 2008-03-31
local variables exist only within the ' space' that they are defined as well as child spaces.

If you've got numerous spaces, e.g. functions, modules, class definitions, do you really want to risk mix-ups with the variables defined in these spaces with similarly named global variables.

Besides if you play too much with global variables, you have to keep track of what's going on with them throughout the program, you get spaghetti code. NOT IDEAL

of course I';m only an amatuer

Ryan

---

### Post by drubin on 2008-03-31
> **rye_ said:**
> 
Besides if you play too much with global variables, you have to keep track of what's going on with them throughout the program, you get spaghetti code. NOT IDEAL

make the functions take in a reference to the variable  &$var... Maybe have a config file with all the default values in an standard array type ie.

[PHP]$config=array();
$config['username']="foo";[/PHP]

---

### Post by The Titan on 2008-03-31
so your saying that is isn't dangerous its just not good practice?

---

### Post by mssever on 2008-04-01
Problems with misusing globals:[LIST=1]
[*]Namespace pollution. As your project grows, there are more names to keep track of, and it becomes more difficult to create good names for stuff. This is the problem with PHP. All of PHP's functions are global, so you end up with abominations such as mysql_real_escape_string().
[*]Accidents happen. What if you forget about some global and reuse it? You'll clobber its original purpose and end up with weird bugs.
[*]As the project grows, it becomes difficult to keep track of what the dark corners of your code are doing with your globals. Best to let them have their own data to work on.
[*]There are few good reasons for using globals (I'm looking at you, PHP and Javascript). The only time I've had a legitamate use is to store configuration data. Even then, though, I still tend to wrap that data up in a class and pass it around whenever possible. You can usually avoid globals easily enough by simply passing the data you need around between functions/methods.
[*]There are probably other reasons that don't come to mind at the moment.[/LIST]

---

### Post by The Titan on 2008-04-01
I appreciate this response, But say i have 1 giant class that controlls all of the ther classes in the site, they are all accessed through this main class.  Is it a bad idea to use this as a global and if so, what should i do instead if i have to use it in a function?

---

### Post by The Titan on 2008-04-01
Bump, Anyone?

---

### Post by mssever on 2008-04-01
> **The Titan said:**
> I appreciate this response, But say i have 1 giant class that controlls all of the ther classes in the site, they are all accessed through this main class.  Is it a bad idea to use this as a global and if so, what should i do instead if i have to use it in a function?

One giant class that controlls everything else probably isn't a good idea to begin with. See [God object]("http://en.wikipedia.org/wiki/God_object"). You should modularize your code so that it falls into smaller chunks which are more robust and easier to maintain.

Now, it's not strictly a bad to have, for example, a global configuration object, but even still, before creating such an object, you need to consider whether you can avoid such a construct altogether.

---

### Post by The Titan on 2008-04-01
> **mssever said:**
> One giant class that controlls everything else probably isn't a good idea to begin with. See [God object]("http://en.wikipedia.org/wiki/God_object"). You should modularize your code so that it falls into smaller chunks which are more robust and easier to maintain.

Now, it's not strictly a bad to have, for example, a global configuration object, but even still, before creating such an object, you need to consider whether you can avoid such a construct altogether.
I think that post was a little misleading, it is broken up into different classes but they are all loaded into the main object to be accessed.  Anyways, thank you for the reply it makes sense now.

---

### Post by tchalvakspam on 2008-10-20
The biggest problem is the unexpected nature of Globals, because you can never rely on them to be exactly what you need.  Just because you run a function and the global value was what you needed once doesn't mean that it will be next time, and the only way you'll find that out will probably come when you're using a function that is using a function that is using a function that is using a global that no longer has the right value, and then debugging becomes a major pain.

Worst: using the global keyword to pull in values from the global namespace outside of functions or classes, you'll regret it as your code grows.
function with_no_parameters(){
global $unexpected_invisible_parameter;
// strange stuff happens here
}

Bad: Using the $_GLOBALS superglobal array to contain anything you want to make available 
function with_no_parameters(){
$unexpected_invisible_parameter = 
      $_GLOBALS['unexpected_invisible_parameter'];
// strange stuff happens here
}

Maybe Better: Use a function with statics to pass settings out only if they're needed.
$website_name = config('website_name');

Much better: Pass a "Registry" or "Configuration" object or some other object that acts as a simple container to hold settings that you don't want to create more than once, and will pass around.  Again, to avoid creating 'em more than once, you can use static variables.
$settings = new WebsiteSettings();
$website_name = $settings->get('website_name');

---

### Post by drubin on 2008-10-20
> **tchalvakspam said:**
> Much better: Pass a "Registry" or "Configuration" object or some other object that acts as a simple container to hold settings that you don't want to create more than once, and will pass around.  Again, to avoid creating 'em more than once, you can use static variables.
$settings = new WebsiteSettings();
$website_name = $settings->get('website_name');

function do_stuff(){
$website_name =? ; //<< Do you create another WebsiteSettings() class every time?, use singletons approach? 

}

---

### Post by mssever on 2008-10-20
> **drubin said:**
> function do_stuff(){
$website_name =? ; //<< Do you create another WebsiteSettings() class every time?, use singletons approach? 

}
I think it often makes sense to use a single, global configuration object. No sense re-creating it every time you need it. You just need to include a way to make sure that you initialize and modify it in a sane, consistent manner.

---

### Post by drubin on 2008-10-20
> **mssever said:**
> I think it often makes sense to use a single, global configuration object. No sense re-creating it every time you need it. You just need to include a way to make sure that you initialize and modify it in a sane, consistent manner.

That was my point how do you suppose you gain access to  $settings, with out using some sort of global/static/singleton approach.

---

### Post by tchalvakspam on 2008-10-27
Choices include:
Passing the settings object around as a parameter to functions,
Using a Registry Singleton (the registry object only gets instantiated once),
Using a static variable in a function that creates and passes back the object.
Using a non-singleton Registry object with statics.


A telling point that I came across when researching solutions to avoid globals is:

Globals are a problem because: They tie your scripts together.  When accessed internally, they create unexpected behavior.
However, a Singleton Registry pattern also has similar problems.  It ties your scripts together.  It can be accessed internally, causing unexpected behavior.
So passing the settings/Registry/whatever object reference when at all possible, to make it obvious that the code is dependent upon the settings object, seems to make a lot of sense.


Personally, I haven't found the magic bullet yet, but at least there are a lot of other options.

---

