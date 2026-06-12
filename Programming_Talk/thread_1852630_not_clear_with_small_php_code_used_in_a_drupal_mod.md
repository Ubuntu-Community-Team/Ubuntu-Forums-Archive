---
title: "not clear with small php code used in a drupal module"
date: 2011-09-30
forum: Programming Talk
---

### Post by jamesbon on 2011-09-30
Here is a small PHP code which  I am not clear with.

```
/**
* Form for configurable Drupal action to beep multiple times
*/
function beep_multiple_beep_action_form($context) {
$form['beeps'] = array(
'#type' => 'textfield',
'#title' => t('Number of beeps'),
'#description' => t('Enter the number of times to beep when this action executes'),
'#default_value' => isset($context['beeps']) ? $context['beeps'] : '1',
'#required' => TRUE,
);
return $form;
}

```
In the above user defined function return $form what does it return? How do you access the individual elements of $form['beeps'] what is the significance of writing beeps in square braces in $form['beeps']
```


function beep_multiple_beep_action_validate($form, $form_state) {
        $beeps = $form_state['values']['beeps'];
        if (!is_int($beeps)) {
        form_set_error('beeps', t('Please enter a whole number between 0 and 10.'));
        }
        else if ((int) $beeps > 10 ) {
        form_set_error('beeps', t('That would be too annoying. Please choose fewer than 10
        beeps.'));
        } else if ((int) $beeps < 0) {
        form_set_error('beeps', t('That would likely create a black hole! Beeps must be a
        positive integer.'));
        }
}


```
In above code what is 
```
        $beeps = $form_state['values']['beeps'];
``` 
line doing?

---

### Post by dazman19 on 2011-09-30
You access data in an array using the [] operators. Likewise in a standard object using -> operator.

in the function below $form['beeps'] is defined to be an array. 
by writing $form['x'] you are actually declaring an array. 

So you have a 2Dimensional array returned from this function. 

To see what it looks like try this die(print_r($form,1)); 

it will probably look like this
Array( 
     [beeps] => Array(
            [#type] => textfield
            [#title] => 5 (assuming t() returns an integer).
     )
)

My advise would be not to make functions with 1 or 2 letter names like t() or w() because  you want to be as descriptive as possible. it makes it easier to read the code, and the less likely chance you will run into scope problems and function over-riding

[PHP]

function beep_multiple_beep_action_form($context) {
$form['beeps'] = array(
'#type' => 'textfield',
'#title' => t('Number of beeps'),
'#description' => t('Enter the number of times to beep when this action executes'),
'#default_value' => isset($context['beeps']) ? $context['beeps'] : '1',
'#required' => TRUE,
);
return $form;

}[/PHP]

Short answer to access the title data in forms you use: 
[PHP]
$form = function beep_multiple_beep_action_form($context);
echo "Title: ".$form['beeps']['#title'];
echo "Type: ".$form['beeps']['#type'];
[/PHP]

Php is a pretty bad language when defining return types. I think 5.4 is looking to allow you to specify return types.

Sounds like homework, but i have already answered this question. Hopefully that is enough for you to figure out the rest.

RTFM here: [http://www.php.net/](http://www.php.net/)

---

### Post by jamesbon on 2011-10-02
Hi, thanks for your message.Actually I am reading a book [www.apress.com/9781430228387](www.apress.com/9781430228387) and trying to become a web programmer so these kind of questions are arising.This kind of code was in Chapter 3 of book.

---

