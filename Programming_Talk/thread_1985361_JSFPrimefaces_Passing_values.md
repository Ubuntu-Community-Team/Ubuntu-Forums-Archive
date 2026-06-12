---
title: "JSF/Primefaces: Passing values?"
date: 2012-05-23
forum: Programming Talk
---

### Post by fallenshadow on 2012-05-23
How can a value as in a variable be passed from one webpage to another while executing code to set and get the value?

MyCode:
```
@ManagedBean(name="TestCodeBean")
public class TestCode {

	@ManagedProperty(value = "#{testValue}")
	private String testValue;

	public String getTestValue() {
		return testValue;
	}

	public void setTestValue(String testValue) {
		this.testValue = testValue;
	}
```


On the starting webpage:
```
<p:inputText  value="#{TestCodeBean.testValue}"></p:inputText>
<p:button action="#{TestCodeBean.testValue}" value="TEST ME"></p:button>
```

On the finishing webpage:
```
<h:outputText value="#{TestCodeBean.testValue}"></h:outputText>
```

What am I doing wrong? :?

---

### Post by fallenshadow on 2012-05-23
As far as I can understand now I just need a proper method to do the transfer and link that to the button.

As for what needs to be in this method I have no idea! :D

---

### Post by r-senior on 2012-05-23
I've not used JSF with annotations but I don't think you need the @ManagedProperty annotation on the instance variable. The properties are implicitly part of the managed bean without needing further annotations.

I think you'd use that @ManagedProperty annotation to dependency inject another managed bean or static value into your managed bean -- similar to the way you would use Spring "ref" properties to refer to other beans as dependencies.

---

### Post by fallenshadow on 2012-05-24
Can anyone see something wrong with this? :?

```
<h:commandButton action="#{TestCodeBean.sendData}" />
```

The error:

> Property 'sendData' not found

Method in TestCodeBean:

```
public String sendData(){
		return "/testOutput.xhtml";
	}
```

---

### Post by r-senior on 2012-05-24
The method name needs to be getSendData(). JSF (like JSTL) uses the implied property name rather than the actual name of the getter/setter.

---

### Post by fallenshadow on 2012-05-25
Yes I got things working now!

I have a value from one page being displayed on my other page. :)

Only quite minor problem I have is that the Primefaces widgets are not themed for some reason. They look like plain JSF widgets but I used primefaces ones. (for example - <p:button></p:button>)

Its only a minor issue though... I don't care.. that much but I do like things that look nice! :D

---

### Post by fallenshadow on 2012-05-29
> Only quite minor problem I have is that the Primefaces widgets are not themed for some reason. They look like plain JSF widgets but I used primefaces ones. (for example - <p:button></p:button>)

Funny how I am kinda replying to myself but just to let ye know that I fixed this problem too!

Make sure to use **<h:head></h:head>** tags instead of **<head></head>** for primefaces! :)

---

