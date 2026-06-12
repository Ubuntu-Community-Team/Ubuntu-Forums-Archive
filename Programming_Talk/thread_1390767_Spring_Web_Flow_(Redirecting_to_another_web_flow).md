---
title: "Spring Web Flow (Redirecting to another web flow)"
date: 2010-01-26
forum: Programming Talk
---

### Post by Crafty Kisses on 2010-01-26
Hey guys, so basically what I'm trying to accomplish here is to redirect my existing flow to a new flow via the action listener, as of right now the code that I have looks something similar to this (just an example as of now):
```
<flow ...>
<var name="myFooHandler" class="x.y.z.FooHandler"/>
...
<view-state id="..." ...>
...
<transition on="foo" to="result">
   <evaluate expression="myFooHandler.getMyCollectionOfBars()" result="flowScope.bars"/>
</transition>
</view-state>

<view-state id="result" ...>
</view-state>
</flow>
```
Now I've seen a very similar thread over at the SpringSource forums, but it hasn't been solved, so this is why I thought I would shoot here. So anyway, I was reading where webflow 2.0 suggests the following:
```
public void myActionListener(ActionEvent event) {
    // Execute any required processing and then forward to the flow execution
    
    facesContext.getCurrentInstance().getExternalContext().dispatch("/spring/main/");
    facesContext.getCurrentInstance().responseComplete();
}
```
Now, I have done that, so my current Spring Web Flow looks something like this:
```
<!-- The front controller of the Spring Web application, responsible for handling all application requests -->
<servlet>
	<servlet-name>Spring Web Servlet</servlet-name>
	<servlet-class>org.springframework.webflow.servlet.SpringWebServlet</servlet-class>
	<init-param>
		<param-name>configLocations</param-name>
		<param-value>/WEB-INF/config/web-application-config.xml</param-value>
	</init-param>
	<load-on-startup>1</load-on-startup>
</servlet>
		
<!-- Map all /spring/* requests to the Spring Web Servlet for handling -->
<servlet-mapping>
	<servlet-name>Spring Web Servlet</servlet-name>
	<url-pattern>/spring/*</url-pattern>
</servlet-mapping>
```
Now before the flow is complete, it needs a response, so I also added:
```
xternalContext externalContext = FacesContext.getCurrentInstance().getExternalContext();
externalContext.redirect(externalContext.getRequestContextPath() + "/jsp/common/DuplicateSubmission.jsf");
```
Then I try to launch the flow execution by doing:
```
<a href="/spring/main">Go</a>
```
Then I notice the flow does not get rendered, so I'm not sure what to do here. I've also tried the following on my managed bean:
```
requestContext.getExternalContext().requestFlowDefinitionRedirect("genericExecute", map);
```
To no avail that does not create a new flow, so I'm stuck. So I'm thinking it could be a couple of issues:

[LIST]
[*]It could be because I'm processing logic in an **actionListener**.
[*]The code is just not right, which it could very possibly be the issue.
[/LIST]

Thanks for the help/advice.

---

### Post by Crafty Kisses on 2010-01-27
Hey, guys so I've actually got the redirecting of flows working, but rather than make another thread, I'd thought I'd post my new problem, if you guys are interested. So as of right now I'm configuring my Web Flow to render JFS, and as of right now my configuration looks perfect, take a look yourself:
[PHP]<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xmlns:webflow="http://www.springframework.org/schema/webflow-config"
       xmlns:faces="http://www.springframework.org/schema/faces"
       xsi:schemaLocation="
           http://www.springframework.org/schema/beans
           http://www.springframework.org/schema/beans/spring-beans-2.5.xsd
           http://www.springframework.org/schema/webflow-config
           http://www.springframework.org/schema/webflow-config/spring-webflow-config-2.0.xsd
           http://www.springframework.org/schema/faces
           http://www.springframework.org/schema/faces/spring-faces-2.0.xsd">[/php]

	[php]<!-- Executes flows: the central entry point into the Spring Web Flow system -->
	<webflow:flow-executor id="flowExecutor" />

	<!-- The registry of executable flow definitions -->
	<webflow:flow-registry id="flowRegistry" flow-builder-services="facesFlowBuilderServices" base-path="/WEB-INF">
		<webflow:flow-location-pattern value="**/*-flow.xml" />
	</webflow:flow-registry>[/php]

	[php]<!-- Configures the Spring Web Flow JSF integration -->
	<faces:flow-builder-services id="facesFlowBuilderServices" />

<h:dataTable id="attemps" styleClass="summary" value="#{attemps}" var="booking" 
             rendered="#{bookings.attemptsCount > 0}">
    <h:column>
        <f:facet name="header">Name</f:facet>

       [/PHP]
I've also noticed I cannot get a parameter from the requestParamter option, so in Eclipse I added the following:
[PHP]
<end-state id="deleteSession">
  <on-entry>
     <evaluate expression="measurementService.deleteSession(requestParameters.sessionId)" />
  </on-entry>
</end-state>[/PHP]
So basically those are the issues I'm encountering in this current flow.

---

### Post by ka3sem on 2010-10-13
@Crafty Kisses
which IDE do you use for spring webflow. I want to use Skyway but I don't know how to install it?

[http://www.skywayperspectives.org/portal/web/guest/downloads/overview]("http://www.skywayperspectives.org/portal/web/guest/downloads/overview")

---

