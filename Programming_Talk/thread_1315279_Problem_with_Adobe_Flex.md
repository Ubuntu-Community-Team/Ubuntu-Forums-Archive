---
title: "Problem with Adobe Flex"
date: 2009-11-05
forum: Programming Talk
---

### Post by nebu on 2009-11-05
here is my code 
```

<?xml version="1.0" encoding="utf-8"?>
<mx:Application xmlns:mx="http://www.adobe.com/2006/mxml" layout="absolute">
	<mx:states>
		<mx:State name="EventRegistration"/>
		<mx:State name="AccoRegistration"/>
		<mx:State name="MakeUser">
			<mx:RemoveChild target="{login}"/>
			<mx:AddChild position="lastChild">
				<mx:RichTextEditor x="200" y="168" title="Title">
				</mx:RichTextEditor>
			</mx:AddChild>
		</mx:State>
		<mx:State name="LoggedIn"/>
	</mx:states>
	<mx:Panel width="250" height="228" layout="absolute" horizontalCenter="0" verticalCenter="0" id="login" title="Login Portal">
		<mx:Label x="82" y="10" text="Username"/>
		<mx:TextInput x="35" y="27" id="username"/>
		<mx:Label x="82" y="57" text="Password"/>
		<mx:TextInput x="35" y="83" id="password" displayAsPassword="true"/>
		<mx:Button x="82" y="113" label="Submit" id="loginButton"/>
		<mx:LinkButton x="50" y="156" label="Not registered yet?" height="22" click="currentState = &quot;EventRegistration&quot;;"/>
	</mx:Panel>
</mx:Application>


```

why is this giving me an error....
i am getting a lot of error messages like
> ProblemType attribute was not a string for marker 94

how do i fix this??

---

### Post by abhilashm86 on 2009-11-05
there is no error in my flex builder, compiled fine, what exactly is error?

---

### Post by nebu on 2009-11-05
the thing is that the items on the make user state do not appear....

try clicking on the not registered yet link....

the error says...
ProblemType attribute was not a string for marker 82
.
.
.
ProblemType attribute was not a string for marker 101

---

### Post by abhilashm86 on 2009-11-05
> **nebu said:**
> the thing is that the items on the make user state do not appear....

try clicking on the not registered yet link....

you have defined states as AccoRegistration, when you click on "not register" LinkButton, where do you want it to navigate? that should go to register page, correct that to
click="currentstate='EventRegistration'"
then it'll work......
i din't understand the concept of using backquotes.........

---

### Post by nebu on 2009-11-05
o really sorry..... i was going to the wrong state

---

