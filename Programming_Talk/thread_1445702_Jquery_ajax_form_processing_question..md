---
title: "Jquery ajax form processing question."
date: 2010-04-02
forum: Programming Talk
---

### Post by hockey97 on 2010-04-02
Hi, I need to understand how to do what I want with jquery ajax to process a form.


Here is what I want to do. I plan to use the .post function from jquery.

I want to grab the forms inputs  which are 2 text boxes and 1 textarea.

I then want to put those values in a variable. I then want put some more extra data in variables.

I then will take all those variables and put it inside .post so it will be sent to a php file. The php file will add the data to the database and if the entry succeeded then it will return true or false depending what it did then the javascript would grab what php will return and then print a error message or a successful message and then load back to main menu.

I already tried to get code working. 

Here is what is happening so far. I already wrote the code 

but when I click submit on the form it would refresh the page or if I specify on the html form the action to the php file. it will redirect to that php file.

I can't get it to just submit the form dynamicly without refreshing or redirecting to another page.

here is the code I have already:```

<script type="text/javascript">
$(document).ready(function(){
$("#submit").click(function() {
 From = <?php echo $user; ?>;
 TO = $('input[name=to_text]');
 Subject = $('input[name=in_text]'); 
 Message = $('textarea[name=data]');
if( TO.val() =="" && Subject.val() =="" && Message.val() ==""){
 html ="<a><b>Error:</b> One field is left blank. Please Fill in all fields and try again.</a>";
$('#write').html(html);
}
else{
$.post("data_center.php", { from:From , to:TO , subject:Subject , message1:Message , db1:"Market" , app_name:"Market_write_messages"}, 
function(data){
if(data == "false"){
           var html='<a>Error:Failed to process your request please try again.</a>';
           $('#write').html(html);}
       else{
         html='<a>Message:You suceeded on Sending a message to: TO.</a>';
           $('#write').html(html);} return false; });       
           setTimeout(function(){open_market_apps('Interested_people','Market','Market_messages');},5000);
});}});}
</script>
```

Any ideas? I know the code is not neat.

---

