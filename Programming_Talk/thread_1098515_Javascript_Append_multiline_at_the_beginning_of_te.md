---
title: "Javascript Append multiline at the beginning of textarea"
date: 2009-03-17
forum: Programming Talk
---

### Post by ztrange on 2009-03-17
Hello, I'm trying to make a javascript function which appends text at the beginnning of the text already in a textarea.

The javascript will be called from a popup and the textarea will be in the parent.

So I will have in the text area

Suponga que $E[X]=5$ y $E[X(X-1)]=27.5$. Calcule:\\
{\it a)} $E[X^2]$; {\it b)} $var(X)$; {\it c)} ?`Cu'al es la relaci'on
entre las cantidades $E[X]$, $E[X(X-1)]$ y $var(X)$.

And after closing the popup I want to have:

\begin{figure}[h!tb]
\epsfig{file=tarea02-2,width=\linewidth} \caption{Histogramas y ojivas para:
el n'umero de horas delante del televisor (\textsl{tvtot}); cantidad
dispuesto a pagar por renta (\textsl{renta}); y valor catastral de la casa
(\textsl{valor}).}
\end{figure}
Suponga que $E[X]=5$ y $E[X(X-1)]=27.5$. Calcule:\\
{\it a)} $E[X^2]$; {\it b)} $var(X)$; {\it c)} ?`Cu'al es la relaci'on
entre las cantidades $E[X]$, $E[X(X-1)]$ y $var(X)$.

So, as you see, i want to append multiple lines that also contain characters like \.

I have this so far but it only works with one line and appends it at the end.

function updateOpener(cadena) {
    opener.document.formFuente.textoProblema.value += cadena;
    window.close();    
}

---

### Post by myrtle1908 on 2009-03-17
To append at the beginning you can do something like ...

[PHP]
function updateOpener(cadena) {
  var s = opener.document.formFuente.textoProblema.value;
  s = cadena + s;
  opener.document.formFuente.textoProblema.value = s;
  window.close();
}
[/PHP]

As to why you are only getting one line ... are you sure that the variable named 'cadena' actually holds the multiline text you require?  Try adding an alert to your function eg.

[PHP]
function updateOpener(cadena) {
  alert(cadena);
  var s = opener.document.formFuente.textoProblema.value;
  s = cadena + s;
  opener.document.formFuente.textoProblema.value = s;
  window.close();
}
[/PHP]

---

### Post by ztrange on 2009-03-17
Thanks for your reply, actually I'm seeing that the javascript function is never called successfully because the alert isn't popping.

This isthe code i use to call the javascript function

[PHP]
$latex_epsfig = "\begin{figure}[h!tb]
                     \epsfig{file=$image,width=\linewidth} \caption{Histogramas y ojivas para:
                     el n'umero de horas delante del televisor (\textsl{tvtot}); cantidad
                     dispuesto a pagar por renta (\textsl{renta}); y valor catastral de la casa
                     (\textsl{valor}).}
                     \end{figure}";
    echo $latex_epsfig;
//Se agrega el bloque de LaTeX al textarea del problema.
?>
	<SCRIPT LANGUAGE="JavaScript">
    updateOpener(<?php echo '"'.$latex_epsfig.'"' ?>)
    </SCRIPT> 
[/PHP]

The echo is showing the correct text, but the alert is not showing. However, if i change the text to be appended for lets say "hello":

[PHP]$latex_epsfig = "hola";[/PHP]

It works fine. So, I'm guessing the problem is with the text and some of the symbols it has: \ }{, etc.

---

### Post by Tibuda on 2009-03-17
> **ztrange said:**
> It works fine. So, I'm guessing the problem is with the text and some of the symbols it has: \ }{, etc.
Replace all \ for \\
\ is a special character in both PHP and JavaScript strings.

---

### Post by ztrange on 2009-03-17
Yes, I think I will need to replace the \. I just tested to pass a single line string:

[PHP]$latex_epsfig = "\begin{figure}[h!tb]";[/PHP]

And it worked almost fine. It showed some rare character instead of \.

Also tested with the same success with this string:

[PHP]$latex_epsfig =  "\begin{figure}[h!tb] \epsfig{file=$image,width";[/PHP]

So I think we can assume that the \ are not the main problem.

Im thinking of doing the append one line at a time backwards.

Edit: Now backslashes are fine:

[PHP]$latex_epsfig = str_replace("\\", "\\\\", $latex_epsfig);[/PHP]

---

### Post by ztrange on 2009-03-19
Well, I finally used the function to append one line at a time. I had to use replace the \ with \\ like the code I pasted before and also had to trim the string to remove some weird trailing character that was causing trouble.

To separate the lines I used explode with \n as the separator. I, then inserted them to the textbox with a javascript. I did it starting form last line.

Also, the line feeds to make the appended text exactly as the original one, I had to insert them directly with javascript.

So, there, my code to work it out is the following:

[PHP]

	$latex_epsfig = "\begin{figure}[h!tb]
                     \centerline{\epsfig{file=$nombreArchivo,width={sglp:anchoImagen}in}}
                     \caption{{sglp:textoCaption}}
                     \end{figure}";
    
    //Sustituimos las \ por \\ para que javascrit funcione, eso no se hace con
    //addslashes porque no queremos tocar los ', solo las \.
    $latex_epsfig = str_replace("\\", "\\\\", $latex_epsfig);

    //Se divide el texto por renglones en un array
    $arrayLatexEpsfig = explode("\n", $latex_epsfig);
    //Se van pegando un renglon a la vez en el textarea, empezando por el ultimo.
    for ($i = count($arrayLatexEpsfig)-1; $i >= 0; $i--){
        $token = $arrayLatexEpsfig[$i];
        ?>
        <SCRIPT LANGUAGE="JavaScript">
            updateOpener(<?php echo '"'.trim($token).'"' ?>)
        </SCRIPT>
        <?php
    }
[/PHP]
I'm sorry the comments are in spanish.

Well, I think taht's it, the javascript function I used for appending is the following:

[PHP]function updateOpener(cadena) {
    //alert(cadena)
    var aux = cadena + "\n" + opener.document.formFuente.<?php echo $textarea ?>.value
    opener.document.formFuente.<?php echo $textarea ?>.value = aux;
}[/PHP]

Thanks for everyone who helped me to sort this out.

---

