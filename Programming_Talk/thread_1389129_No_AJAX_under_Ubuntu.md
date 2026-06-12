---
title: "No AJAX under Ubuntu?"
date: 2010-01-24
forum: Programming Talk
---

### Post by jubantu on 2010-01-24
Hi,

I made a Grails application that uses simple AJAX calls. After testing it on various systems (Windows/Ubuntu) with various browsers (IE, FF, Opera), I learned that it is not working under Ubuntu, neither with FF nor with Opera. Both browsers seem to have no support for AJAX under Ubuntu? I also checked my Firebug console and it is reporting that "AJAX is undefined". Well, maybe it is possible that it is just a matter of tuning some system properties in Ubuntu. What can I check? Is there any AJAX support under Ubuntu 9.10 at all? BTW, it works perfectly under Windows with all browsers.

I found out that other people have similar problems. See here:

[http://www.webmasterworld.com/linux/4040346.htm](http://www.webmasterworld.com/linux/4040346.htm)

Does anybody have a solution yet?

Thanks,
jubantu

---

### Post by denarced on 2010-01-24
That's funny. I thought ajax was javascript so in that sense client-side. OS should have nothing to do with it unless you're also using apache under Ubuntu and running your scripts from there..

---

### Post by jubantu on 2010-01-24
Are you sure it has nothing to do with the OS? 
The link to the other thread I have included in my post (see above) suggests otherwise. BTW, I have no Apache running under Ubuntu. Grails however comes with an embedded Jetty (resp. Tomcat) server.

---

### Post by Ryan Dwyer on 2010-01-24
AJAX works fine in Ubuntu. You can try checking Firefox's error console to see what's going on. Chrome has some sort of javascript debugger as well but I don't know how to use it.

---

### Post by jubantu on 2010-01-24
I have already checked the Firebug console in Firefox. It says "AJAX is undefined". JavaScript, however, is enabled.

---

### Post by denarced on 2010-01-24
> **jubantu said:**
> Are you sure it has nothing to do with the OS? 
The link to the other thread I have included in my post (see above) suggests otherwise. BTW, I have no Apache running under Ubuntu. Grails however comes with an embedded Jetty (resp. Tomcat) server.

I mean nothing to do in the sense that firefox handles ajax alone as ajax is just javascript connected to a database somewhere else. It might be possible that team-ubuntu deliveres a modified firefox as a part of ubuntu but still , it should have nothing to do with OS.

---

### Post by Hellkeepa on 2010-01-24
HELLo!

"AJAX" I reckon is your variable, and if it's undefined then it means that the code that's meant to set it has not been executed. However, without seeing an example of the code that doesn't work, we can't help you any further.

Happy codin'!

---

### Post by myrtle1908 on 2010-01-24
Most likely case sensitivity issues with your JavaScript includes.

Edit: Use Firebug to check for 404s on your JS includes.

---

### Post by jubantu on 2010-01-24
> **denarced said:**
> It might be possible that team-ubuntu deliveres a modified firefox as a part of ubuntu but still , it should have nothing to do with OS.

Are you suggesting that the current Ubuntu distribution of Firefox might be the problem? Where can I find out if that is the case? 
What is with Opera on Ubuntu then? AJAX calls are also not working under Ubuntu.

The code is perfectly working on Windows (Vista/XP).

---

### Post by Ryan Dwyer on 2010-01-24
Post your code, please.

---

### Post by wieman01 on 2010-01-24
I can confirm it works under Ubuntu, otherwise I would not be able to read a ever increasing number of websites and could not develop my own Ajax-applications. It works just fine, no problems whatsoever.

Happy programming!

---

### Post by jubantu on 2010-01-24
> **wieman01 said:**
> I can confirm it works under Ubuntu

The strangest thing is that AJAX powered websites are working with Firefox 3.5.7 under Ubuntu 9.10. Maybe the problem lays within the Grails internals that handle the JavaScript/AJAX stuff behind the scenes. But this would be out of my scope. (BTW, I make use of the prototype library)

One commenter stated it might be a problem with case sensitivity. 
I'm absolutely sure the code I have here is correct. It is a tutorial from a recent Grails book and it works on Windows. 

What I need are some hints where to investigate first. The problem could be in Ubuntu, FF or Grails.

Has anybody read the discussion under [http://www.webmasterworld.com/linux/4040346.htm](http://www.webmasterworld.com/linux/4040346.htm) yet? It implies that the current FF package is not "serving" AJAX under Ubuntu. It seems like a very recent issue maybe package version related.

I also attached the error message I got from my Firebug console. Maybe this leads to further hint to solve the issue:

```
Ajax is undefined
function onclick(event) { new (Ajax.Updater)("details", "/MyApp/message/showDetails/23", {asynchronous: true, evalScripts: true}); return false; }()1 (Zeile 2)
[Break on this error] new (Ajax.Updater)("details", ...nchronous: true, evalScripts: true});
```

---

### Post by Hellkeepa on 2010-01-24
HELLo!

The code you posted seems to be using a library, if you haven't included this library then it's no wonder "Ajax" isn't defined. It's not something that is standard to browsers, after all. Browsers use the "XHtmlRequest" object.
When I said "example", I didn't mean the one line which is giving the error, but a working minimalistic example showing the exact same error as you're having.

The thread you linked to provided no useful information either, other than there was this one guy who couldn't get "AJAX" to work. That's like saying I can't get my vehicle to work, just as useful for a mechanic across the other side of the world.

Happy codin'!

---

### Post by Ryan Dwyer on 2010-01-24
> **jubantu said:**
> "details", ...nchronous: true

If that's your actual code, then you need to type asynchronous.

EDIT: As well as the other stuff.

---

### Post by Hellkeepa on 2010-01-24
HELLo!

That's not a part of the code, **Ryan Dwyer**, but the error message.

Happy codin'!

---

### Post by wieman01 on 2010-01-24
jubantu, 

Would you mind posting your code? What library (e.g. JQuery) are you using?

---

### Post by jubantu on 2010-01-24
Sure, here is the code. I'm using the Prototype library.

This is my GSP file from where the asynchronous call is being made:

```

<%@ page import="Message" %>
<html>
    <head>
        <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
        <meta name="layout" content="main" />
        <g:javascript library="prototype" />
        <title><g:message code="default.list.label" args="[entityName]" /></title>
    </head>
    <body>
        <div class="nav">
            <span class="menuButton"><a class="home" href="${resource(dir: '')}">Home</a></span>
            <span class="menuButton"><g:link class="create" action="create" params='["event.id":"${event?.id}"]'><g:message code="default.new.label" args="[entityName]" /></g:link></span>
        </div>

        <div class="body">
          <h1>${event?.name} - Forum Messages</h1>
          <div id="messageList">
            <g:each in="${messageInstanceList}" var="messageInstance">
              <g:remoteLink action="showDetails" id="${messageInstance?.id}" update="details">
                ${messageInstance.author.fullName} - ${messageInstance.subject}
              </g:remoteLink>
            </g:each>
          </div>
          <h3>Message Details</h3>
          <div id="details">
          </div>
        </div>

    </body>
</html>

```

This is the _details.gsp template file that should be loaded into the <div id="details"> section of the above GSP file.

```

<div class="dialog">
  <table>
    <tr class="prop">
      <td valign="top" class="name"><g:message code="message.subject.label" default="Subject"/></td>

      <td valign="top" class="value">${fieldValue(bean: messageInstance, field: "subject")}</td>

    </tr>

    <tr class="prop">
      <td valign="top" class="name"><g:message code="message.content.label" default="Content"/></td>

      <td valign="top" class="value">${fieldValue(bean: messageInstance, field: "content")}</td>

    </tr>

    <tr class="prop">
      <td valign="top" class="name"><g:message code="message.author.label" default="Author"/></td>

      <td valign="top" class="value">${fieldValue(bean: messageInstance, field: "author")}</td>

    </tr>
  </table>

  <div class="buttons">
    <span class="menuButton">
      <g:link class="create" action="reply" id="${messageInstance?.id}">
        Reply
      </g:link>
    </span>
  </div>

</div>

```

My Controller Action:

```

def showDetails = {
        def messageInstance = Message.get(params.id)
        if(messageInstance){
            render(template:"details", model:['messageInstance':messageInstance])
        }
        else {
            render "No message found with id: ${params.id}"
        }
    }

```

---

### Post by jubantu on 2010-02-03
UODATE: 

It seems that Ubuntu does not like the prototype library. Recently I checked out the generated HTML by viewing the page's source. I only found the expected line of
 
```
<script type="text/javascript" src="/MyApp/js/prototype/prototype.js"></script>
```

under all browsers in Windows. On Ubuntu however the prototype library is not being included at all. Neither in FF, Opera, nor Google Chrome. So I guess this is either a Grails (maybe a case sensitivity issues somewhere?) or an Ubuntu issue. Hope someone can help.

---

### Post by Hellkeepa on 2010-02-03
HELLo!

I'm willing to bet that this is a case sensitivity issue, or a case of a wrong path. Remember that while Windows is not case sensitive, all *nix based OSes are.

Happy codin'!

---

### Post by myrtle1908 on 2010-02-03
> **jubantu said:**
> So I guess this is either a Grails (**maybe a case sensitivity issues somewhere?**) or an Ubuntu issue. Hope someone can help.

Have you tried using Firebug to check for 404s?

---

