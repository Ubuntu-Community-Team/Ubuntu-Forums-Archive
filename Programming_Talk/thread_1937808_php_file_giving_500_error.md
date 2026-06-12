---
title: "php file giving 500 error"
date: 2012-03-08
forum: Programming Talk
---

### Post by AstroLlama on 2012-03-08
I've been trying to make a wordpress theme from scratch, but when I open the index.php page in localhost I get an http 500 error. 

Apache is installed and configured correctly (Another site I have displays just fine). 

the only difference is that the index.php of the old site begins with an HTML declaration.

header.php contains the proper declarations shouldn't this be enough?

navigating to localhost/new_site/index.php gives 500 error:
```

<?php get_header(); ?>
    
<div id="main">
  <div id="content">
    <h1>Main Area</h1>
    <?php if (have_posts()) : while (have_posts()) : the_post(); ?>
    <h1><?php the_title(); ?></h1>
    <h4>Posted on <?php the_time('F jS, Y') ?></h4>
    <p><?php the_content(__('(more...)')); ?></p>
    <hr>
    <?php endwhile; else: ?>
    <p><?php _e('Sorry, no posts matched your criteria.'); ?></p>
    <?php endif; ?>
  </div>

  <?php get_sidebar(); ?>

  </div>

<div id="delimiter"></div>

<?php get_footer(); ?>

```

I've been trying to start this new site but am frustrated that right at stage 1 I can't even view the page correctly on my computer... any suggestions?

---

### Post by dazman19 on 2012-03-09
could be any number of reasons. I don't know what any of the functions do so I cant be certain.

Firstly you need to check the log. Turn on error reporting by doing this, [PHP]<?php 
error_reporting(E_ALL);
?>[/PHP] 

It will most likely be here so you want to:

sudo tail -n50 /var/log/apache2/error.log

About 90% of the time PHP is getting fatal errors.

Syntactically the code you posted seems ok. However I would use die('test'); through each bits of the code to see where the execution is failing, starting at the top going down once you have exhausted fixing the problems in the error log.

---

