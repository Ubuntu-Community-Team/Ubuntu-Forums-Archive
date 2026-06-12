---
title: "compiling scss into css for the first time"
date: 2014-09-02
forum: Programming Talk
---

### Post by Drone4four on 2014-09-02
I’m trying to setup sass/scss for the first time.  I installed ruby-sass with apt.  

[Here]("http://refills.bourbon.io/type-systems/") is some sample code from bourbon.io.

Here is the sample html:

```


<head>
  <link href='http://fonts.googleapis.com/css?family=Radley:400,400italic' rel='stylesheet' type='text/css'>
  <link href='http://fonts.googleapis.com/css?family=Noto+Sans:400,700,400italic,700italic' rel='stylesheet' type='text/css'>
  <link rel="stylesheet" type="text/css" href="css/main.css" /> 
</head>

<article class="type-system-traditional">
  <p class="type">Article Type</p>
  <h1>Article Heading</h1>
  <h2>These override some of the styles specified in the <code>_variables.scss</code> and <code>_typography.scss</code> partials in <a href="//bitters.bourbon.io">Bitters</a>. You can replace the typography variables and the header font specifications in Bitters with these styles. Then you won&rsquo;t need the wrapping class <code>.type-system-name</code>.</h2>
  <p class="date">30 Mar 2014</p>
  <p><span>Lorem ipsum dolor sit amet</span>, consectetur adipisicing elit. Consequatur a, ullam, voluptatum incidunt neque doloremque vel inventore distinctio laudantium harum</a> illo quam nulla dolor alias iure impedit! Accusamus! Lorem ipsum dolor sit amet, consectetur adipisicing elit. Accusamus! Lorem ipsum dolor sit amet, consectetur adipisicing elit. Consequatur, a, ullam, voluptatum incidunt neque porro numquam doloremque vel inventore distinctio laudantium harum illo quam nulla dolor alias iure impedit.
    <a href="javascript:void(0)" class="read-more">Read More <span>&rsaquo;</span></a>
  </p>
  <h3>Subheading lorem</h3>
  <p><span>Consequatur ullam, voluptatum</span> incidunt neque porro numquam doloremque vel inventore distinctio laudantium harum illo quam nulla dolor alias iure impedit. Accusamus. Consequatur, a, ullam, voluptatum incidunt neque porro numquam doloremque vel inventore distinctio laudantium harum illo quam nulla dolor alias iure impedit! Accusamus.</p>
  <hr>
  <p class="author">Author Name</p>
</article>


```
Here is the scss:
```

@import "compass/utilities";
@import "compass/css3";
   
article.type-system-traditional {
  $sans-serif: 'Noto Sans', sans-serif;
  $serif: 'Radley', serif;

  @include clearfix;
  text-align: left;

  .type {
    border-bottom: 2px solid;
    display: inline-block;
    font-family: $sans-serif;
    font-size: .7em;
    font-weight: 800;
    margin-bottom: 2em;
    padding: .1em 0;
    text-align: left;
    text-transform: uppercase;
  }

  h1 {
    font-family: $serif;
    font-size: 1.9em;
    font-weight: 700;
    margin-bottom: .3em;

    @include media($medium-screen) {
      font-size: 2.6em;
    }
  }

  h2 {
    font-family: $serif;
    font-size: 1.3em;
    font-weight: 400;
    line-height: 1.25em;
    margin-bottom: .9em;

    @include media($medium-screen) {
      font-size: 1.5em;
    }
  }

  code {
    white-space: nowrap;
    background: #F7F7F7;
    border: 1px solid #E0E0E0;
    border-radius: $base-border-radius * 1.5;
    padding: .1em .4em;
    font-size: .75em;
    font-style: normal;
  }

  h2 code {
    font-size: .65em;
  }

  h3 {
    font-family: $serif;
    font-size: 1.4em;
    font-style: italic;
    font-weight: 400;
    line-height: 1.3em;
    margin-bottom: .4em;
  }

  p.date {
    color: transparentize($base-font-color, .6);
    font-family: $serif;
    font-style: italic;
    margin-bottom: .3em;
  }

  p {
    font-family: $sans-serif;
    letter-spacing: 1;
    margin-bottom: 1.5em;
    line-height: 1.55em;

    span {
      font-family: $serif;
      font-size: 1.2em;
      font-style: italic;
    }
  }
  
  a.read-more {
    display: inline-block;
    font-family: $sans-serif;
    font-weight: 700;
    font-size: .8em;
    text-transform: uppercase;
    margin-left: .2em;
    position: relative;

    span {
      font-family: $sans-serif;
      font-style: normal;
      position: absolute;
      font-size: 1.5em;
      top: -1px;
      right: -12px;
    }
  }

  hr {
    width: 3em;
  }

  p.author {
    font-family: $serif;
    font-size: 1.2em;
    font-style: italic;
  }
}

```
When I try to compile it, I get this message:
```

$ sass main.scss
Syntax error: File to import not found or unreadable: compass/utilities.
              Load path: ~/Dropbox/TECH/my_sites/inspiration_from_others/bourbon_type_systems/css
        on line 1 of main.scss
  Use --trace for backtrace.
$ 
```
With the same code sample but with the semicolons on line 1 and 2 removed, I get this error:
```

$ scss main.scss
Syntax error: Invalid CSS after "...pass/utilities"": expected selector or at-rule, was "@import "compas..."
        on line 2 of main.scss
  Use --trace for backtrace.
$ 

```

[Here]("http://codepen.io/anon/pen/Ejmix") is the code on codepen.

I gather that I’m not importing compass correctly.  How do I correctly import compass and compile the scss into css? What am I doing wrong?

---

### Post by Dimarchi on 2014-09-07
You haven't created a compass project, that is what. :)

For personal education I went through this thing and found just the same stuff as you did. I removed imports, mixins, and defined some variables for testing both sass and scss commands. Both worked just fine. Just a while ago I took a look at compass, and this is what I did to get the stuff working (terminal stuff, obviously):

```
compass create test
```

test in above is the project name in the path of your choice. Modify it to your liking.  When you create the project you get some info along with the command. According to it you should now move main.scss to the sass subdirectory of your new project. Read the other stuff, too. After you are done with that, you compile your project. In my case, the project is in /home/dimarchi/test. Thus:

```
compass compile /home/dimarchi/test
```

You should now have a perfectly working compass processed main.css in the stylesheets subdirectory of your project!

Hopefully this answers your question.

---

### Post by Drone4four on 2014-09-07
Thank-you, **Dimarchi**.

I installed ruby-compass.  I created a test directory with compass create test:
```
$ compass create test
directory test/ 
directory test/sass/ 
directory test/stylesheets/ 
   create test/config.rb 
   create test/sass/screen.scss 
   create test/sass/print.scss 
   create test/sass/ie.scss 
   create test/stylesheets/screen.css 
   create test/stylesheets/ie.css 
   create test/stylesheets/print.css 

*********************************************************************
Congratulations! Your compass project has been created.

You may now add and edit sass stylesheets in the sass subdirectory of your project.

Sass files beginning with an underscore are called partials and won't be
compiled to CSS, but they can be imported into other sass stylesheets.

You can configure your project by editing the config.rb configuration file.

You must compile your sass stylesheets into CSS when they change.
This can be done in one of the following ways:
  1. To compile on demand:
     compass compile [path/to/project]
  2. To monitor your project for changes and automatically recompile:
     compass watch [path/to/project]

More Resources:
  * Website: http://compass-style.org/
  * Sass: http://sass-lang.com
  * Community: http://groups.google.com/group/compass-users/


To import your new stylesheets add the following lines of HTML (or equivalent) to your webpage:
<head>
  <link href="/stylesheets/screen.css" media="screen, projection" rel="stylesheet" type="text/css" />
  <link href="/stylesheets/print.css" media="print" rel="stylesheet" type="text/css" />
  <!--[if IE]>
      <link href="/stylesheets/ie.css" media="screen, projection" rel="stylesheet" type="text/css" />
  <![endif]-->
</head>
$ 
```
So far so good.  I then placed my sample from bourbon.io main.scss file into the sass directory, as you suggested, **Dimarchi**.  I then executed the compile command:
```
$ compass compile test/
unchanged test/sass/screen.scss
    error test/sass/main.scss (Line 29: Undefined mixin 'media'.)
   create test/stylesheets/main.css 
unchanged test/sass/ie.scss
unchanged test/sass/print.scss
$

```
So I open up main.scss and locate Line 29.   Here is Line 29-31:
```
@include media($medium-screen) {
      font-size: 2.6em;
    }

```
I’m not sure what a Mixin is.  The sass-lang.com guide says this about Mixins:
> Some things in CSS are a bit tedious to write, especially with CSS3 and the many vendor prefixes that exist. A mixin lets you make groups of CSS declarations that you want to reuse throughout your site. You can even pass in values to make your mixin more flexible. A good use of a mixin is for vendor prefixes. Here's an example for border-radius.
SCS SYNTAX:
```

@mixin border-radius($radius) {
  -webkit-border-radius: $radius;
     -moz-border-radius: $radius;
      -ms-border-radius: $radius;
          border-radius: $radius;
}

.box { @include border-radius(10px); }

```
To create a mixin you use the @mixin directive and give it a name. We've named our mixin border-radius. We're also using the variable $radius inside the parentheses so we can pass in a radius of whatever we want. After you create your mixin, you can then use it as a CSS declaration starting with @include followed by the name of the mixin. When your CSS is generated it'll look like this:
```

.box {
  -webkit-border-radius: 10px;
  -moz-border-radius: 10px;
  -ms-border-radius: 10px;
  border-radius: 10px;
}

```


So mixins saves the web designer time by grouping CSS declarations that can be reused.  In my case on Line 29, the Mixin is the import of media with the $medium-screen parameter that can vary.  I’m not sure how this line should render in css or how media medium-screen could vary (like what the possible variables could be).  I see that the doc authors passed the 10px parameter to the border-radius function with the .box class: ```
 .box { @include border-radius(10px); } 
```  Line 29 in main.scss that I am playing with sort of looks similar.  Here is Line 29-31 again:
```

    @include media($medium-screen) {
      font-size: 2.6em;
	}

```
I figure I can’t pass a parameter to the media function because before media is an import selector(@include)  rather than a class(.include or in the case of the sass docs, .box).  I looked up media types at w3schools and learned that the @media rule can have different layouts for screen, print, mobile phone, tablet, but I felt silly inputting print in place of $medium-screen.  

Here is the erroneous main .css compass generated:
```

/*
Syntax error: Undefined mixin 'media'.
        on line 29 of /home/gnull/Dropbox/TECH/my_sites/inspiration_from_others/bourbon_type_systems/test/sass/main.scss, in `media'
        from line 29 of /home/gnull/Dropbox/TECH/my_sites/inspiration_from_others/bourbon_type_systems/test/sass/main.scss

Backtrace:
/home/gnull/Dropbox/TECH/my_sites/inspiration_from_others/bourbon_type_systems/test/sass/main.scss:29:in `media'
/home/gnull/Dropbox/TECH/my_sites/inspiration_from_others/bourbon_type_systems/test/sass/main.scss:29
/usr/lib/ruby/vendor_ruby/sass/tree/visitors/perform.rb:253:in `visit_mixin'
/usr/lib/ruby/vendor_ruby/sass/tree/visitors/base.rb:37:in `visit'
/usr/lib/ruby/vendor_ruby/sass/tree/visitors/perform.rb:100:in `visit'
/usr/lib/ruby/vendor_ruby/sass/tree/visitors/base.rb:53:in `block in visit_children'
/usr/lib/ruby/vendor_ruby/sass/tree/visitors/base.rb:53:in `map'
/usr/lib/ruby/vendor_ruby/sass/tree/visitors/base.rb:53:in `visit_children'
/usr/lib/ruby/vendor_ruby/sass/tree/visitors/perform.rb:109:in `block in visit_children'
/usr/lib/ruby/vendor_ruby/sass/tree/visitors/perform.rb:121:in `with_environment'
/usr/lib/ruby/vendor_ruby/sass/tree/visitors/perform.rb:108:in `visit_children'
/usr/lib/ruby/vendor_ruby/sass/tree/visitors/base.rb:37:in `block in visit'
/usr/lib/ruby/vendor_ruby/sass/tree/visitors/perform.rb:320:in `visit_rule'
/usr/lib/ruby/vendor_ruby/sass/tree/visitors/base.rb:37:in `visit'
/usr/lib/ruby/vendor_ruby/sass/tree/visitors/perform.rb:100:in `visit'
/usr/lib/ruby/vendor_ruby/sass/tree/visitors/base.rb:53:in `block in visit_children'
/usr/lib/ruby/vendor_ruby/sass/tree/visitors/base.rb:53:in `map'
/usr/lib/ruby/vendor_ruby/sass/tree/visitors/base.rb:53:in `visit_children'
/usr/lib/ruby/vendor_ruby/sass/tree/visitors/perform.rb:109:in `block in visit_children'
/usr/lib/ruby/vendor_ruby/sass/tree/visitors/perform.rb:121:in `with_environment'
/usr/lib/ruby/vendor_ruby/sass/tree/visitors/perform.rb:108:in `visit_children'
/usr/lib/ruby/vendor_ruby/sass/tree/visitors/base.rb:37:in `block in visit'
/usr/lib/ruby/vendor_ruby/sass/tree/visitors/perform.rb:320:in `visit_rule'
/usr/lib/ruby/vendor_ruby/sass/tree/visitors/base.rb:37:in `visit'
/usr/lib/ruby/vendor_ruby/sass/tree/visitors/perform.rb:100:in `visit'
/usr/lib/ruby/vendor_ruby/sass/tree/visitors/base.rb:53:in `block in visit_children'
/usr/lib/ruby/vendor_ruby/sass/tree/visitors/base.rb:53:in `map'
/usr/lib/ruby/vendor_ruby/sass/tree/visitors/base.rb:53:in `visit_children'
/usr/lib/ruby/vendor_ruby/sass/tree/visitors/perform.rb:109:in `block in visit_children'
/usr/lib/ruby/vendor_ruby/sass/tree/visitors/perform.rb:121:in `with_environment'
/usr/lib/ruby/vendor_ruby/sass/tree/visitors/perform.rb:108:in `visit_children'
/usr/lib/ruby/vendor_ruby/sass/tree/visitors/base.rb:37:in `block in visit'
/usr/lib/ruby/vendor_ruby/sass/tree/visitors/perform.rb:128:in `visit_root'
/usr/lib/ruby/vendor_ruby/sass/tree/visitors/base.rb:37:in `visit'
/usr/lib/ruby/vendor_ruby/sass/tree/visitors/perform.rb:100:in `visit'
/usr/lib/ruby/vendor_ruby/sass/tree/visitors/perform.rb:7:in `visit'
/usr/lib/ruby/vendor_ruby/sass/tree/root_node.rb:20:in `render'
/usr/lib/ruby/vendor_ruby/sass/engine.rb:315:in `_render'
/usr/lib/ruby/vendor_ruby/sass/engine.rb:262:in `render'
/usr/lib/ruby/vendor_ruby/compass/compiler.rb:140:in `block (2 levels) in compile'
/usr/lib/ruby/vendor_ruby/compass/compiler.rb:126:in `timed'
/usr/lib/ruby/vendor_ruby/compass/compiler.rb:139:in `block in compile'
/usr/lib/ruby/vendor_ruby/compass/logger.rb:45:in `red'
/usr/lib/ruby/vendor_ruby/compass/compiler.rb:138:in `compile'
/usr/lib/ruby/vendor_ruby/compass/compiler.rb:118:in `compile_if_required'
/usr/lib/ruby/vendor_ruby/compass/compiler.rb:103:in `block (2 levels) in run'
/usr/lib/ruby/vendor_ruby/compass/compiler.rb:101:in `each'
/usr/lib/ruby/vendor_ruby/compass/compiler.rb:101:in `block in run'
/usr/lib/ruby/vendor_ruby/compass/compiler.rb:126:in `timed'
/usr/lib/ruby/vendor_ruby/compass/compiler.rb:100:in `run'
/usr/lib/ruby/vendor_ruby/compass/commands/update_project.rb:45:in `perform'
/usr/lib/ruby/vendor_ruby/compass/commands/base.rb:18:in `execute'
/usr/lib/ruby/vendor_ruby/compass/commands/project_base.rb:19:in `execute'
/usr/lib/ruby/vendor_ruby/compass/exec/sub_command_ui.rb:43:in `perform!'
/usr/lib/ruby/vendor_ruby/compass/exec/sub_command_ui.rb:15:in `run!'
/usr/bin/compass:30:in `block in <main>'
/usr/bin/compass:44:in `call'
/usr/bin/compass:44:in `<main>'
*/
body:before {
  white-space: pre;
  font-family: monospace;
  content: "Syntax error: Undefined mixin 'media'.\A         on line 29 of /home/gnull/Dropbox/TECH/my_sites/inspiration_from_others/bourbon_type_systems/test/sass/main.scss, in `media'\A         from line 29 of /home/gnull/Dropbox/TECH/my_sites/inspiration_from_others/bourbon_type_systems/test/sass/main.scss"; }

```

---

### Post by Dimarchi on 2014-09-08
Yeah, wondered why my main.scss went through without trouble after your posting...turns out I had been using my cleaned up version of the file.

After checking this out, it looks like some of the stuff has nothing to do with either sass or compass - they are things refills referred to in bourbon, bitters, and/or neat. Using media as a mixin name is unfortunate (though valid as a mixin name): you might confuse it with @media...therefore in the main.scss that works I replaced it with another name. That mixin still uses @media in the end, if you take a look at the resulting main.css file. I defined two other variables, too, that cause errors.

Here is the working main.scss using none of the bourbon etc. stuff:

```
@import "compass/utilities";
@import "compass/css3";

@mixin example-mix($size) {
  @if $size == large {
    @media (min-width: 64.375em) { @content; }
  }
  @else if $size == medium {
    @media (min-width: 50em) { @content; }
  }
  @else if $size == small {
    @media (min-width: 37.5em)  { @content; }
  }
}

$base-border-radius: 10px;
$base-font-color: black;
   
article.type-system-traditional {
  $sans-serif: 'Noto Sans', sans-serif;
  $serif: 'Radley', serif;

  @include clearfix;
  text-align: left;

  .type {
    border-bottom: 2px solid;
    display: inline-block;
    font-family: $sans-serif;
    font-size: .7em;
    font-weight: 800;
    margin-bottom: 2em;
    padding: .1em 0;
    text-align: left;
    text-transform: uppercase;
  }

  h1 {
    font-family: $serif;
    font-size: 1.9em;
    font-weight: 700;
    margin-bottom: .3em;

    @include example-mix(medium) {
      font-size: 2.6em;
    }
  }

  h2 {
    font-family: $serif;
    font-size: 1.3em;
    font-weight: 400;
    line-height: 1.25em;
    margin-bottom: .9em;

    @include example-mix(medium) {
      font-size: 1.5em;
    }
  }

  code {
    white-space: nowrap;
    background: #F7F7F7;
    border: 1px solid #E0E0E0;
    border-radius: $base-border-radius * 1.5;
    padding: .1em .4em;
    font-size: .75em;
    font-style: normal;
  }

  h2 code {
    font-size: .65em;
  }

  h3 {
    font-family: $serif;
    font-size: 1.4em;
    font-style: italic;
    font-weight: 400;
    line-height: 1.3em;
    margin-bottom: .4em;
  }

  p.date {
    color: transparentize($base-font-color, .6);
    font-family: $serif;
    font-style: italic;
    margin-bottom: .3em;
  }

  p {
    font-family: $sans-serif;
    letter-spacing: 1;
    margin-bottom: 1.5em;
    line-height: 1.55em;

    span {
      font-family: $serif;
      font-size: 1.2em;
      font-style: italic;
    }
  }
  
  a.read-more {
    display: inline-block;
    font-family: $sans-serif;
    font-weight: 700;
    font-size: .8em;
    text-transform: uppercase;
    margin-left: .2em;
    position: relative;

    span {
      font-family: $sans-serif;
      font-style: normal;
      position: absolute;
      font-size: 1.5em;
      top: -1px;
      right: -12px;
    }
  }

  hr {
    width: 3em;
  }

  p.author {
    font-family: $serif;
    font-size: 1.2em;
    font-style: italic;
  }
}
```

How about now, does it work?

---

### Post by Drone4four on 2014-09-08
Thank-you **Dimarchi**

Your scss file compiled perfectly and now the css it produced makes my html look amazing parsed in my browser.  

Before I move on though, I still have a few comments/questions. 

One question in my mind involves clicking on the placeholder 'Bitters' link on the sample webpage.  Hovering over the link in my browser indicates that it should take me to the the TLD at bourbon.io (file://bitters.bourbon.io/).  But when I click the link, it takes me to my local root folder.  At first this made me jump, but then I figured I don't have to worry because I am viewing the html file locally.  It's not posted on my live digital ocean droplet.  Anyways, why and how does clicking the link in my browser take me to my local root folder?  I figure it has something to do with the file:// prefix.

I wasn't sure what you meant by refills and neat.  So I went to bourbin.io and learned that those are modules and open source projects developed by the team on bourbin.io.  I didn't take a good hard long look at refills and neat.  I saw enough to conclude that refills and neat are more for intermediate web designers.  I'm not there yet.  Maybe later when I have a little more experience.  

Suffice to say that I now have a working css file for me to learn from.  I can now borrow and adapt the css file produced from the compiled sample which you've kindly helped me with, **Dimarchi**.  Thanks again.

---

### Post by michael171 on 2014-09-08
I wanted to add that the reason the link trys to load a file from your local machine is what you expect, the file: in this case is the scheme or protocol, that tells the browser what kind of resource it is and what type of language should be used.  file would indicate that you are refering to a file or folder on your local machine whereas http: would indicate a hypertext transfer protocol used to communicate html and markup files over the internet.  [http://bitters.bourbon.io/](http://bitters.bourbon.io/) would link to the website because of http.  If you look at [http://en.wikipedia.org/wiki/Uniform_resource_locator](http://en.wikipedia.org/wiki/Uniform_resource_locator) under syntax you will see scheme://domain:port/path?query_string#fragment_id and the explanation of what scheme is.

---

### Post by Drone4four on 2014-09-09
I sorta already knew that the prefix at the beginning of the URL indicates the protocol.  Although I wouldn't have been able to articulate an explanation off the top of my head for how URLs work the way you did, **mcihael171**.  So thank-you.  

I uploaded the html and css to my webserver and discovered that the browser directs to [http://bitters.bourbon.io/](http://bitters.bourbon.io/), not file://bitters.bourbon.io/ . The reason for this is that Chrome defaults to the context of how the webpage is being viewed.  For me I initially clicked the link locally in Chrome directly from my Dropbox folder (hence, file://) where as when viewing the webpage in Chrome on the worldwideweb, it defaulted to http:// .

---

### Post by Dimarchi on 2014-09-09
You're welcome.:)

michael171 kindly provided enough info on URLs, so I don't have to. As for browsers...Chrome (and other Webkit based browsers? I don't remember offhand) tends to have that thing with files (local vs. localhost/hosted). One of the reasons to have other browsers in hand for testing, as well.

---

