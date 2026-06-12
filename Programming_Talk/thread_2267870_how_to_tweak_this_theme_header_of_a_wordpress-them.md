---
title: "how to tweak this theme header of a wordpress-theme?"
date: 2015-03-04
forum: Programming Talk
---

### Post by dilbert_one on 2015-03-04
can i create a div block - as a container for a shortcode 

run a wordpess version 4.1 - with a theme called responsive and a Meta-Slider in the theme header: see the demo at [http://www.ex-libri.org](http://www.ex-libri.org) 

see the free space at the right of the slider (which contains some book-images) I want to add another image - or thing that is being added by shortcode - newsfeed from a facebook-feed. 

i want to add this with a shortcode in the theme 


How do I make a basic div block in the theme-header?  


This is the code for a basic div:

```
<div id=layer1 style="position:absolute; top:20; left:20; width:300; height:300; z-index:1; padding:5px; border: #000000 2px solid; background-color:#000000; background-image:url(yourfilename.gif); layer-background-image:url(yourfilename.gif);">

Content goes here (images, text) - a shortcode in  wordpress

</div>
```

Some ideas regarding the div element: 

> What is a div element?    
A div element is a block of content that can be positioned anywhere on your site by using absolute positioning and the <div> tag. 
The purpose of div elements is to hold content, whereas frames hold pages. This content can be placed anywhere on your site and 
it can even overlap. The content can consist of images or html. 
All of the style elements like scrollbar color and font color can be controlled by a simple style sheet.
 

here the full code 

```


<?php

// Exit if accessed directly
if( !defined( 'ABSPATH' ) ) {
    exit;
}

/**
 * Header Template
 *
 *
 * @file           header.php
 * @package        Responsive
 * @author         Emil Uzelac
 * @copyright      2003 - 2014 CyberChimps
 * @license        license.txt
 * @version        Release: 1.3
 * @filesource     wp-content/themes/responsive/header.php
 * @link           http://codex.wordpress.org/Theme_Development#Document_Head_.28header.php.29
 * @since          available since Release 1.0
 */
?>
    <!doctype html>
    <!--[if !IE]>
    <html class="no-js non-ie" <?php language_attributes(); ?>> <![endif]-->
    <!--[if IE 7 ]>
    <html class="no-js ie7" <?php language_attributes(); ?>> <![endif]-->
    <!--[if IE 8 ]>
    <html class="no-js ie8" <?php language_attributes(); ?>> <![endif]-->
    <!--[if IE 9 ]>
    <html class="no-js ie9" <?php language_attributes(); ?>> <![endif]-->
    <!--[if gt IE 9]><!-->
<html class="no-js" <?php language_attributes(); ?>> <!--<![endif]-->
    <head>

        <meta charset="<?php bloginfo( 'charset' ); ?>"/>
        <meta name="viewport" content="width=device-width, initial-scale=1.0">

        <title><?php wp_title( '&#124;', true, 'right' ); ?></title>

        <link rel="profile" href="http://gmpg.org/xfn/11"/>
        <link rel="pingback" href="<?php bloginfo( 'pingback_url' ); ?>"/>

        <?php wp_head(); ?>
    </head>

<body <?php body_class(); ?>>

<?php responsive_container(); // before container hook ?>
<div id="container" class="hfeed">
    <div class="skip-container cf">
        <a class="skip-link screen-reader-text focusable" href="#content"><?php _e( '&darr; Skip to Main Content', 'responsive' ); ?></a>
    </div><!-- .skip-container -->
<?php responsive_header(); // before header hook ?>
    <div id="header">

        <?php responsive_header_top(); // before header content hook ?>

        <?php if( has_nav_menu( 'top-menu', 'responsive' ) ) { ?>
            <?php wp_nav_menu( array(
                                   'container'      => '',
                                   'fallback_cb'    => false,
                                   'menu_class'     => 'top-menu',
                                   'theme_location' => 'top-menu'
                               )
            );
            ?>
        <?php } ?>

        <?php responsive_in_header(); // header hook ?>

        <?php if( get_header_image() != '' ) : ?>

            <div id="logo">
                <a href="<?php echo home_url( '/' ); ?>"><img src="<?php header_image(); ?>" width="<?php echo get_custom_header()->width; ?>" height="<?php echo get_custom_header()->height; ?>" alt="<?php bloginfo( 'name' ); ?>"/></a>
            </div><!-- end of #logo -->

        <?php endif; // header image was removed ?>

        <?php if( !get_header_image() ) : ?>

            <div id="logo">
                <span class="site-name"><a href="<?php echo home_url( '/' ); ?>" title="<?php echo esc_attr( get_bloginfo( 'name', 'display' ) ); ?>" rel="home"><?php bloginfo( 'name' ); ?></a></span>
                <span class="site-description"><?php bloginfo( 'description' ); ?></span>
            </div><!-- end of #logo -->

        <?php endif; // header image was removed (again) ?>

        <?php get_sidebar( 'top' ); ?>
        <?php wp_nav_menu( array(
                               'container'       => 'div',
                               'container_class' => 'main-nav',
                               'fallback_cb'     => 'responsive_fallback_menu',
                               'theme_location'  => 'header-menu'
                           )
        );
        ?>

        <?php if( has_nav_menu( 'sub-header-menu', 'responsive' ) ) { ?>
            <?php wp_nav_menu( array(
                                   'container'      => '',
                                   'menu_class'     => 'sub-header-menu',
                                   'theme_location' => 'sub-header-menu'
                               )
            );
            ?>
        <?php } ?>

        <?php responsive_header_bottom(); // after header content hook ?>

    </div><!-- end of #header -->
<?php responsive_header_end(); // after header container hook ?>
<?php

echo do_shortcode("[metaslider id=112]");
?>
<?php responsive_wrapper(); // before wrapper container hook ?>
    <div id="wrapper" class="clearfix">
<?php responsive_wrapper_top(); // before wrapper content hook ?>
<?php responsive_in_wrapper(); // wrapper hook ?>



```


 note - this is the line with the meta slider that is currently  visilble
echo do_shortcode("[metaslider id=112]");


love to hear from yoiu

---

