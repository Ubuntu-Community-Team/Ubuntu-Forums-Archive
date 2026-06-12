---
title: "[jQuery] Creating array from selectors"
date: 2009-07-09
forum: Programming Talk
---

### Post by Pyro.699 on 2009-07-09
So, i have this section of html:

[html]
<input type="text" id="inputA_1" value="ValueA" />
<input type="text" id="inputB_1" value="ValueB" />
<input type="text" id="inputC_1" value="ValueC" />
<input type="text" id="inputD_1" value="ValueD" />
[/html]And i want to build this basic java script variable
[html]
var postdata = {inputA: 'ValueA',
    inputB: 'ValueB',
    inputC: 'ValueC',
    inputD: 'ValueD'}
[/html]In reality there are approximately 100 variables. (Its a template builder).

Currently im doing it like this
[html]
function buildPostData(id){
    var postdata = {inputA: $("#inputA_"+id).val(), inputB: $("#inputB_"+id).val(), inputC: $("#inputC_"+id).val(), inputD: $("#inputD_"+id).val()};
}
[/html]Now, i KNOW there is a better way to do this. Im just not 100% sure on how to use the array.push function properly.

Here is what i have so far:
[html]
function buildPostData(id){
    var postdata = [];
    $("input[id$='_"+id+"']").each(function(){
        var id = $(this).attr("id");
        var value = $(this).val();
        
        //Now how to i push it into the array properly?
        postdata.push(id: value);
    });
}
[/html]Thanks alot
~Cody Woolaver

---

### Post by myrtle1908 on 2009-07-09
I haven't got JQuery at hand however in your example 'postdata' is not an Array (rather an Object) so you cannot 'push' onto it.

Observe the following:-

[PHP]<script>
var postdata = {};
var data = [
	'inputA=ValueA',
	'inputB=ValueB',
	'inputC=ValueC'
];
for (var i=0; i<data.length; i++) {
	var d = data[i].split('=');
	postdata[d[0]] = d[1];
}
alert(postdata.inputA);
</script>[/PHP]

See the line 'postdata[d[0]] = d[1];', here we are setting an object property eg. postdata.inputA = ValueA

---

