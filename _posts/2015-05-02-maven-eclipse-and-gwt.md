---
layout: post
title: Starting with Maven Eclipse and GWT 
description: Maven and gwt starting error workaround through eclipse 
comments: true
---

When you start with GWT one of the first things you may want to do is bind your project with maven. Luckily GWT is very well suited for this task, there is a maven plugin that will help you in many cases.

One of the better utilities this plugin offers you is the gwt archetype: 

`mvn archetype:generate -DarchetypeGroupId=org.codehaus.mojo -DarchetypeArtifactId=gwt-maven-plugin -DarchetypeVersion=2.7.0`

Set your properties and is done. The next step is check if everything is ok so in the dir you have created type `mvn gwt:run`. All seems ok util you go to the browser and Boom! 404 error. index.html (or whatever) not found.

There are many workarounds for this issue, the one in witch I am more productive is using Eclipse IDE and running from it. 

To achieve this, first you have to install the gwt eclipse plugin, second eclipsify the project using `mvn eclipse:eclipse` and import the project to the IDE, finally, configure it like the following:

- Open project properties (alt + intr) and go to google menu item and select Web Application. Check the checkbox named "This projects has a war directory". With this eclipse should be able to find your index.html.
- Next go to Web Toolkit and check "Use Google Web Toolkit".
- At this point eclipse should be able to run correctly the project as a web application but if you modify the server part you will find that changes doesn't take effect. So to fix this the best workaround I have found is mark the dir target/generate-sources as source folder (right click, "Build Path", "use as source folder"). Yep, ugly but works.
 
The last point has some troubles: for example, if you clean your project the target folder is erased so you will have to eclipsify the project and set generate-sources folder as a source again. Hopefully, in GWT projects you probably will not need to do this frequently.
