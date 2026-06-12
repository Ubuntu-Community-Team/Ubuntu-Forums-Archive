---
title: "ubuntu touch development - changes to the code do not change program when ran"
date: 2014-11-13
forum: New to Ubuntu
---

### Post by jarreed0 on 2014-11-13
When every I make a an application in the Ubuntu SDK, such as a scope, html5 app, and app, and edit some of the code and run it will not always change.
For example when I edit the appearance in the scope ini file nothing changes, but I am able to change the header in the ini file.
When I create a new scope project without doing anything to it I get this error:
```
 [COLOR=#1414be][FONT=Monospace]Starting /usr/bin/unity-scope-tool...[/FONT][/COLOR]
 [COLOR=#be1414][FONT=Monospace]scoperegistry: no remote registry configured, only local scopes will be available[/FONT][/COLOR]
 [COLOR=#3c3c3c][FONT=Monospace]RegistryObject::ScopeProcess::exec(): Process for scope: "Kickstarter-scope" started[/FONT][/COLOR]
 [COLOR=#be1414][FONT=Monospace]file:///usr/share/unity8/Dash/DashContent.qml:100: TypeError: Cannot read property 'loaded' of null[/FONT][/COLOR]
 [COLOR=#be1414][FONT=Monospace]file:///usr/share/unity8/ScopeTool.qml:77:31: Unable to assign [undefined] to scopes_ng::Scope*[/FONT][/COLOR]
 [COLOR=#be1414][FONT=Monospace]file:///usr/share/unity8/ScopeTool.qml:149:23: Unable to assign null to QString[/FONT][/COLOR]
 [COLOR=#be1414][FONT=Monospace]
[/FONT][/COLOR]
 [COLOR=#be1414][FONT=Monospace](unity-scope-tool:9915): GLib-GObject-CRITICAL **: g_object_unref: assertion 'G_IS_OBJECT (object)' failed[/FONT][/COLOR]
 [COLOR=#be1414][FONT=Monospace]file:///usr/lib/x86_64-linux-gnu/qt5/qml/Ubuntu/Components/Themes/Ambiance/TabBarStyle.qml:303: TypeError: Property 'select' of object QQuickRepeater(0xd3c090) is not a function[/FONT][/COLOR]
 [COLOR=#be1414][FONT=Monospace]file:///usr/share/unity8/Dash/DashContent.qml:100: TypeError: Cannot read property 'loaded' of null[/FONT][/COLOR]
 [COLOR=#be1414][FONT=Monospace]file:///usr/share/unity8/Dash/CardFilterGrid.qml:36:5: QML FilterGrid: Binding loop detected for property "height"[/FONT][/COLOR]
 [COLOR=#be1414][FONT=Monospace]file:///usr/share/unity8/Dash/CardFilterGrid.qml:36:5: QML FilterGrid: Binding loop detected for property "height"[/FONT][/COLOR]
 [COLOR=#be1414][FONT=Monospace]file:///usr/share/unity8/Dash/CardFilterGrid.qml:36:5: QML FilterGrid: Binding loop detected for property "height"[/FONT][/COLOR]
 [COLOR=#be1414][FONT=Monospace]file:///usr/share/unity8/Dash/CardFilterGrid.qml:36:5: QML FilterGrid: Binding loop detected for property "height"[/FONT][/COLOR]
 [COLOR=#be1414][FONT=Monospace]file:///usr/share/unity8/Dash/CardFilterGrid.qml:36:5: QML FilterGrid: Binding loop detected for property "height"[/FONT][/COLOR]
 [COLOR=#be1414][FONT=Monospace]file:///usr/share/unity8/Dash/Card.qml:102:16: QML Image: Cannot open: file:///usr/share/unity8/Dash/icon[/FONT][/COLOR]
 [COLOR=#be1414][FONT=Monospace]file:///usr/share/unity8/Dash/CardFilterGrid.qml:36:5: QML FilterGrid: Binding loop detected for property "height"[/FONT][/COLOR]
 [COLOR=#be1414][FONT=Monospace]file:///usr/share/unity8/Dash/CardFilterGrid.qml:36:5: QML FilterGrid: Binding loop detected for property "height"[/FONT][/COLOR]
 [COLOR=#3c3c3c][FONT=Monospace]RegistryObject::ScopeProcess::on_process_death(): Process for scope: "Kickstarter-scope" terminated[/FONT][/COLOR]
 [COLOR=#1414be][FONT=Monospace]/usr/bin/unity-scope-tool exited with code 0[/FONT][/COLOR]


```

I cant seem to find anything to fix any of these errors.

Here it the error with the basic app:
```
 [COLOR=#1414be][FONT=Monospace]Starting /usr/lib/x86_64-linux-gnu/qt5/bin/qmlscene...[/FONT][/COLOR]
 [COLOR=#be1414][FONT=Monospace]unity::action::ActionManager::ActionManager(QObject*):[/FONT][/COLOR]
 [COLOR=#be1414][FONT=Monospace]	Could not determine application identifier. HUD will not work properly.[/FONT][/COLOR]
 [COLOR=#be1414][FONT=Monospace]	Provide your application identifier in $APP_ID environment variable.[/FONT][/COLOR]
 [COLOR=#be1414][FONT=Monospace]
[/FONT][/COLOR]
 [COLOR=#be1414][FONT=Monospace]** (qmlscene:12040): WARNING **: Unable to register app: GDBus.Error:org.freedesktop.DBus.Error.InvalidArgs: Invalid application ID[/FONT][/COLOR]
 [COLOR=#1414be][FONT=Monospace]/usr/lib/x86_64-linux-gnu/qt5/bin/qmlscene exited with code 0[/FONT][/COLOR]


```

Here is the error for an HTML5 app:
```
 [COLOR=#1414be][FONT=Monospace]Starting /usr/bin/ubuntu-html5-app-launcher...[/FONT][/COLOR]
 [COLOR=#be1414][FONT=Monospace]Setting import path to:  /home/avery/untitled/www/../lib/x86_64-linux-gnu [/FONT][/COLOR]
 [COLOR=#be1414][FONT=Monospace]
[/FONT][/COLOR]
 [COLOR=#be1414][FONT=Monospace]WARNING: This project is using the experimental QML API extensions for QtWebKit and is therefore tied to a specific QtWebKit release.[/FONT][/COLOR]
 [COLOR=#be1414][FONT=Monospace]WARNING: The experimental API will change from version to version, or even be removed. You have been warned![/FONT][/COLOR]
 [COLOR=#be1414][FONT=Monospace]
[/FONT][/COLOR]
 [COLOR=#be1414][FONT=Monospace]unity::action::ActionManager::ActionManager(QObject*):[/FONT][/COLOR]
 [COLOR=#be1414][FONT=Monospace]	Could not determine application identifier. HUD will not work properly.[/FONT][/COLOR]
 [COLOR=#be1414][FONT=Monospace]	Provide your application identifier in $APP_ID environment variable.[/FONT][/COLOR]
 [COLOR=#be1414][FONT=Monospace]Cannot create CordovaView object.[/FONT][/COLOR]
 [COLOR=#be1414][FONT=Monospace]Falling back on the plain Webview backend.[/FONT][/COLOR]
 [COLOR=#be1414][FONT=Monospace]Inspector server started successfully. Try pointing a WebKit browser to http://192.168.1.5:9221[/FONT][/COLOR]
 [COLOR=#be1414][FONT=Monospace]
[/FONT][/COLOR]
 [COLOR=#be1414][FONT=Monospace]** (ubuntu-html5-app-launcher:12090): WARNING **: Unable to register app: GDBus.Error:org.freedesktop.DBus.Error.InvalidArgs: Invalid application ID[/FONT][/COLOR]
 [COLOR=#be1414][FONT=Monospace]Injecting webapps script[0] : file:///usr/lib/x86_64-linux-gnu/qt5/qml/Ubuntu/UnityWebApps/unity-webapps-api.js[/FONT][/COLOR]
 [COLOR=#1414be][FONT=Monospace]/usr/bin/ubuntu-html5-app-launcher exited with code 0[/FONT][/COLOR]


```

I cant find any fixes to these errors.
I even tried the soundcloud tutorial scope and that to gives errors and when ran only shows the header that says Soundcloud instead of the picture and the appearance is standard instead of the soundcloud appearance and it does not show anything else.

Any help would be appreciated.
Thank You

-Avery Reed

---

