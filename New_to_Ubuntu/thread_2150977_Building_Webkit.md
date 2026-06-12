---
title: "Building Webkit"
date: 2013-06-03
forum: New to Ubuntu
---

### Post by adityaharish on 2013-06-03
I'm trying to build WebKit in Ubuntu (12.04 )
I can '*configure*' it successfully but when I try to  '*make*' it ,it's showing some error .

Code:
[SIZE=2]**ketan@ketan-HP-dx2480-MT-KL969AV:~/Downloads/WebKit-r145184$ make**[/SIZE]
[SIZE=2]**  GEN    DerivedSources/webkit/webkitenumtypes.cpp**[/SIZE]
[SIZE=2]**  GEN    stamp-webkitenumtypes.h**[/SIZE]
[SIZE=2]**  GEN    DerivedSources/WebCore/JSSVGExternalResourcesRequired.h**[/SIZE]
[SIZE=2]**  GEN    DerivedSources/WebCore/JSSVGFilterPrimitiveStandardAttributes.h**[/SIZE]
[SIZE=2]**  GEN    DerivedSources/WebCore/JSSVGFitToViewBox.h**[/SIZE]
[SIZE=2]**  GEN    DerivedSources/WebCore/JSSVGLangSpace.h**[/SIZE]
[SIZE=2]**  GEN    DerivedSources/WebCore/JSSVGLocatable.h**[/SIZE]
[SIZE=2]**  GEN    DerivedSources/WebCore/JSSVGTests.h**[/SIZE]
[SIZE=2]**  GEN    DerivedSources/WebCore/JSSVGTransformable.h**[/SIZE]
[SIZE=2]**  GEN    DerivedSources/WebCore/JSSVGURIReference.h**[/SIZE]
[SIZE=2]**  GEN    generate-webkit2-forwarding-headers**[/SIZE]
[SIZE=2]**  GEN    generate-webkit2-forwarding-headers**[/SIZE]
[SIZE=2]**  GEN    generate-webkittestrunner-forwarding-headers**[/SIZE]
[SIZE=2]**  GEN    generate-webkittestrunner-forwarding-headers**[/SIZE]
[SIZE=2]**  GEN    generate-testwebkitapi-forwarding-headers**[/SIZE]
[SIZE=2]**  GEN    generate-testwebkitapi-forwarding-headers**[/SIZE]
[SIZE=2]**  GEN    DerivedSources/JavaScriptCore/LLIntAssembly.h**[/SIZE]
[SIZE=2]**offlineasm: Parsing ./Source/JavaScriptCore/llint/LowLevelInterpreter.asm and Programs/LLIntOffsetsExtractor and creating assembly file DerivedSources/JavaScriptCore/LLIntAssembly.h.**[/SIZE]
[SIZE=2]**offlineasm: No magic values found. Skipping assembly file generation.**[/SIZE]
[SIZE=2]**make  all-am**[/SIZE]
[SIZE=2]**make[1]: Entering directory `/home/ketan/Downloads/WebKit-r145184'**[/SIZE]
[SIZE=2]**  CXX    Source/WebKit/gtk/WebCoreSupport/libwebkitgtk_3_0_la-InspectorClientGtk.lo**[/SIZE]
[SIZE=2]**  CXX    Source/WebKit/gtk/webkit/libwebkitgtk_3_0_la-webkitversion.lo**[/SIZE]
[SIZE=2]**  CXX    Source/WebKit/gtk/webkit/libwebkitgtk_3_0_la-webkitwebsettings.lo**[/SIZE]
[SIZE=2]**  CXX    DerivedSources/webkit/libwebkitgtk_3_0_la-webkitenumtypes.lo**[/SIZE]
[SIZE=2]**  CXX    Source/WebCore/bindings/js/libWebCore_la-JSCSSValueCustom.lo**[/SIZE]
[SIZE=2]**  CXX    Source/WebCore/bindings/js/libWebCore_la-JSDOMBinding.lo**[/SIZE]
[SIZE=2]**  CXX    Source/WebCore/bindings/js/libWebCore_la-JSEventCustom.lo**[/SIZE]
[SIZE=2]**  CXX    Source/WebCore/bindings/js/libWebCore_la-JSEventTargetCustom.lo**[/SIZE]
[SIZE=2]**  CXX    Source/WebCore/bindings/js/libWebCore_la-JSExceptionBase.lo**[/SIZE]
[SIZE=2]**  CXX    DerivedSources/WebCore/libWebCore_la-EventFactory.lo**[/SIZE]
[SIZE=2]**  CXX    DerivedSources/WebCore/libWebCore_la-JSDOMWindow.lo**[/SIZE]
[SIZE=2]**  CXX    DerivedSources/WebCore/libWebCore_la-JSSVGDocument.lo**[/SIZE]
[SIZE=2]**  CXXLD  libWebCore.la**[/SIZE]
[SIZE=2]**  CXX    Source/WebCore/bindings/js/libWebCoreSVG_la-JSSVGElementInstanceCustom.lo**[/SIZE]
[SIZE=2]**  CXX    Source/WebCore/bindings/js/libWebCoreSVG_la-JSSVGLengthCustom.lo**[/SIZE]
[SIZE=2]**  CXX    Source/WebCore/bindings/js/libWebCoreSVG_la-JSSVGPathSegCustom.lo**[/SIZE]
[SIZE=2]**  CXX    DerivedSources/WebCore/libWebCoreSVG_la-JSSVGAElement.lo**[/SIZE]
[SIZE=2]**  CXX    DerivedSources/WebCore/libWebCoreSVG_la-JSSVGAltGlyphDefElement.lo**[/SIZE]
[SIZE=2]**  CXX    DerivedSources/WebCore/libWebCoreSVG_la-JSSVGAltGlyphElement.lo**[/SIZE]
[SIZE=2]**  CXX    DerivedSources/WebCore/libWebCoreSVG_la-JSSVGAltGlyphItemElement.lo**[/SIZE]
[SIZE=2]**  CXX    DerivedSources/WebCore/libWebCoreSVG_la-JSSVGAnimateColorElement.lo**[/SIZE]
[SIZE=2]**  CXX    DerivedSources/WebCore/libWebCoreSVG_la-JSSVGAnimatedLength.lo**[/SIZE]
[SIZE=2]**  CXX    DerivedSources/WebCore/libWebCoreSVG_la-JSSVGAnimatedLengthList.lo**[/SIZE]
[SIZE=2]**  CXX    DerivedSources/WebCore/libWebCoreSVG_la-JSSVGAnimatedNumberList.lo**[/SIZE]
[SIZE=2]**  CXX    DerivedSources/WebCore/libWebCoreSVG_la-JSSVGAnimatedPreserveAspectRatio.lo**[/SIZE]
[SIZE=2]**  CXX    DerivedSources/WebCore/libWebCoreSVG_la-JSSVGAnimatedRect.lo**[/SIZE]
[SIZE=2]**  CXX    DerivedSources/WebCore/libWebCoreSVG_la-JSSVGAnimatedTransformList.lo**[/SIZE]
[SIZE=2]**  CXX    DerivedSources/WebCore/libWebCoreSVG_la-JSSVGAnimateElement.lo**[/SIZE]
[SIZE=2]**  CXX    DerivedSources/WebCore/libWebCoreSVG_la-JSSVGAnimateMotionElement.lo**[/SIZE]
[SIZE=2]**  CXX    DerivedSources/WebCore/libWebCoreSVG_la-JSSVGAnimateTransformElement.lo**[/SIZE]
[SIZE=2]**  CXX    DerivedSources/WebCore/libWebCoreSVG_la-JSSVGAnimationElement.lo**[/SIZE]
[SIZE=2]**  CXX    DerivedSources/WebCore/libWebCoreSVG_la-JSSVGCircleElement.lo**[/SIZE]
[SIZE=2]**  CXX    DerivedSources/WebCore/libWebCoreSVG_la-JSSVGClipPathElement.lo**[/SIZE]
[SIZE=2]**  CXX    DerivedSources/WebCore/libWebCoreSVG_la-JSSVGComponentTransferFunctionElement.lo**[/SIZE]
[SIZE=2]**  CXX    DerivedSources/WebCore/libWebCoreSVG_la-JSSVGCursorElement.lo**[/SIZE]
[SIZE=2]**  CXX    DerivedSources/WebCore/libWebCoreSVG_la-JSSVGDefsElement.lo**[/SIZE]
[SIZE=2]**  CXX    DerivedSources/WebCore/libWebCoreSVG_la-JSSVGDescElement.lo**[/SIZE]
[SIZE=2]**  CXX    DerivedSources/WebCore/libWebCoreSVG_la-JSSVGElement.lo**[/SIZE]
[SIZE=2]**  CXX    DerivedSources/WebCore/libWebCoreSVG_la-JSSVGElementInstance.lo**[/SIZE]
[SIZE=2]**  CXX    DerivedSources/WebCore/libWebCoreSVG_la-JSSVGElementWrapperFactory.lo**[/SIZE]
[SIZE=2]**  CXX    DerivedSources/WebCore/libWebCoreSVG_la-JSSVGEllipseElement.lo**[/SIZE]
[SIZE=2]**  CXX    DerivedSources/WebCore/libWebCoreSVG_la-JSSVGFEBlendElement.lo**[/SIZE]
[SIZE=2]**  CXX    DerivedSources/WebCore/libWebCoreSVG_la-JSSVGFEColorMatrixElement.lo**[/SIZE]
[SIZE=2]**  CXX    DerivedSources/WebCore/libWebCoreSVG_la-JSSVGFEComponentTransferElement.lo**[/SIZE]
[SIZE=2]**  CXX    DerivedSources/WebCore/libWebCoreSVG_la-JSSVGFECompositeElement.lo**[/SIZE]
[SIZE=2]**  CXX    DerivedSources/WebCore/libWebCoreSVG_la-JSSVGFEConvolveMatrixElement.lo**[/SIZE]
[SIZE=2]**  CXX    DerivedSources/WebCore/libWebCoreSVG_la-JSSVGFEDiffuseLightingElement.lo**[/SIZE]
[SIZE=2]**  CXX    DerivedSources/WebCore/libWebCoreSVG_la-JSSVGFEDisplacementMapElement.lo**[/SIZE]
[SIZE=2]**  CXX    DerivedSources/WebCore/libWebCoreSVG_la-JSSVGFEDropShadowElement.lo**[/SIZE]
[SIZE=2]**  CXX    DerivedSources/WebCore/libWebCoreSVG_la-JSSVGFEFloodElement.lo**[/SIZE]
[SIZE=2]**  CXX    DerivedSources/WebCore/libWebCoreSVG_la-JSSVGFEGaussianBlurElement.lo**[/SIZE]
[SIZE=2]**  CXX    DerivedSources/WebCore/libWebCoreSVG_la-JSSVGFEImageElement.lo**[/SIZE]
[SIZE=2]**  CXX    DerivedSources/WebCore/libWebCoreSVG_la-JSSVGFEMergeElement.lo**[/SIZE]
[SIZE=2]**  CXX    DerivedSources/WebCore/libWebCoreSVG_la-JSSVGFEMorphologyElement.lo**[/SIZE]
[SIZE=2]**  CXX    DerivedSources/WebCore/libWebCoreSVG_la-JSSVGFEOffsetElement.lo**[/SIZE]
[SIZE=2]**  CXX    DerivedSources/WebCore/libWebCoreSVG_la-JSSVGFESpecularLightingElement.lo**[/SIZE]
[SIZE=2]**  CXX    DerivedSources/WebCore/libWebCoreSVG_la-JSSVGFETileElement.lo**[/SIZE]
[SIZE=2]**  CXX    DerivedSources/WebCore/libWebCoreSVG_la-JSSVGFETurbulenceElement.lo**[/SIZE]
[SIZE=2]**  CXX    DerivedSources/WebCore/libWebCoreSVG_la-JSSVGFilterElement.lo**[/SIZE]
[SIZE=2]**  CXX    DerivedSources/WebCore/libWebCoreSVG_la-JSSVGForeignObjectElement.lo**[/SIZE]
[SIZE=2]**  CXX    DerivedSources/WebCore/libWebCoreSVG_la-JSSVGGElement.lo**[/SIZE]
[SIZE=2]**  CXX    DerivedSources/WebCore/libWebCoreSVG_la-JSSVGGlyphRefElement.lo**[/SIZE]
[SIZE=2]**  CXX    DerivedSources/WebCore/libWebCoreSVG_la-JSSVGGradientElement.lo**[/SIZE]
[SIZE=2]**  CXX    DerivedSources/WebCore/libWebCoreSVG_la-JSSVGImageElement.lo**[/SIZE]
[SIZE=2]**  CXX    DerivedSources/WebCore/libWebCoreSVG_la-JSSVGLinearGradientElement.lo**[/SIZE]
[SIZE=2]**  CXX    DerivedSources/WebCore/libWebCoreSVG_la-JSSVGLineElement.lo**[/SIZE]
[SIZE=2]**  CXX    DerivedSources/WebCore/libWebCoreSVG_la-JSSVGMarkerElement.lo**[/SIZE]
[SIZE=2]**  CXX    DerivedSources/WebCore/libWebCoreSVG_la-JSSVGMaskElement.lo**[/SIZE]
[SIZE=2]**  CXX    DerivedSources/WebCore/libWebCoreSVG_la-JSSVGMissingGlyphElement.lo**[/SIZE]
[SIZE=2]**  CXX    DerivedSources/WebCore/libWebCoreSVG_la-JSSVGPathElement.lo**[/SIZE]
[SIZE=2]**  CXX    DerivedSources/WebCore/libWebCoreSVG_la-JSSVGPathSegArcAbs.lo**[/SIZE]
[SIZE=2]**  CXX    DerivedSources/WebCore/libWebCoreSVG_la-JSSVGPathSegArcRel.lo**[/SIZE]
[SIZE=2]**  CXX    DerivedSources/WebCore/libWebCoreSVG_la-JSSVGPathSegClosePath.lo**[/SIZE]
[SIZE=2]**  CXX    DerivedSources/WebCore/libWebCoreSVG_la-JSSVGPatternElement.lo**[/SIZE]
[SIZE=2]**  CXX    DerivedSources/WebCore/libWebCoreSVG_la-JSSVGPolygonElement.lo**[/SIZE]
[SIZE=2]**  CXX    DerivedSources/WebCore/libWebCoreSVG_la-JSSVGPolylineElement.lo**[/SIZE]
[SIZE=2]**  CXX    DerivedSources/WebCore/libWebCoreSVG_la-JSSVGRadialGradientElement.lo**[/SIZE]
[SIZE=2]**  CXX    DerivedSources/WebCore/libWebCoreSVG_la-JSSVGRectElement.lo**[/SIZE]
[SIZE=2]**  CXX    DerivedSources/WebCore/libWebCoreSVG_la-JSSVGStopElement.lo**[/SIZE]
[SIZE=2]**  CXX    DerivedSources/WebCore/libWebCoreSVG_la-JSSVGSVGElement.lo**[/SIZE]
[SIZE=2]**  CXX    DerivedSources/WebCore/libWebCoreSVG_la-JSSVGTextElement.lo**[/SIZE]
[SIZE=2]**  CXXLD  libWebCoreSVG.la**[/SIZE]
[SIZE=2]**  CXXLD  libwebkitgtk-3.0.la**[/SIZE]
[SIZE=2]**  CXX    Source/WebKit2/UIProcess/API/gtk/libwebkit2gtk_3_0_la-WebKitVersion.lo**[/SIZE]
[SIZE=2]**  CXXLD  libwebkit2gtk-3.0.la**[/SIZE]
[SIZE=2]**  CXX    Source/WebCore/testing/js/libWebCoreInternals_la-WebCoreTestSupport.lo**[/SIZE]
[SIZE=2]**  CXX    DerivedSources/WebCore/libWebCoreInternals_la-JSInternals.lo**[/SIZE]
[SIZE=2]**  CXX    DerivedSources/WebCore/libWebCoreInternals_la-JSInternalSettings.lo**[/SIZE]
[SIZE=2]**  CXXLD  libWebCoreInternals.la**[/SIZE]
[SIZE=2]**  CXX    Source/WebKit2/UIProcess/API/gtk/tests/Libraries_libWebKit2APITestCore_la-LoadTrackingTest.lo**[/SIZE]
[SIZE=2]**  CXX    Source/WebKit2/UIProcess/API/gtk/tests/Libraries_libWebKit2APITestCore_la-WebKitTestServer.lo**[/SIZE]
[SIZE=2]**  CXX    Source/WebKit2/UIProcess/API/gtk/tests/Libraries_libWebKit2APITestCore_la-WebViewTest.lo**[/SIZE]
[SIZE=2]**  CXXLD  Libraries/libWebKit2APITestCore.la**[/SIZE]
[SIZE=2]**  CXXLD  Libraries/libTestRunnerInjectedBundle.la**[/SIZE]
[SIZE=2]**  CXXLD  Programs/WebKitPluginProcess**[/SIZE]
[SIZE=2]**/bin/mkdir -p ./.deps/DerivedSources**[/SIZE]
[SIZE=2]**  CXXLD  Programs/WebKitWebProcess**[/SIZE]
[SIZE=2]**./.libs/libwebkit2gtk-3.0.so: undefined reference to `gdk_screen_get_monitor_workarea'**[/SIZE]
[SIZE=2]**./.libs/libwebkit2gtk-3.0.so: undefined reference to `gdk_event_get_scroll_deltas'**[/SIZE]
[SIZE=2]**collect2: error: ld returned 1 exit status**[/SIZE]
[SIZE=2]**make[1]: *** [Programs/WebKitWebProcess] Error 1**[/SIZE]
[SIZE=2]**make[1]: Leaving directory `/home/ketan/Downloads/WebKit-r145184'**[/SIZE]
[SIZE=2]**make: *** [all] Error 2**[/SIZE]


Can anyone please help me in solving this error ??

---

### Post by dave0109 on 2013-06-03
How much do you know about compiling stuff?

> ./.libs/libwebkit2gtk-3.0.so: undefined reference to `gdk_screen_get_monitor_workarea'
This means that the source you're compiling it refering to something that is not defined by other source files in the project, or other headers files that it's including.  You should search for that string and find out why you don't have it.

E.g. Do you have the right dependencies installed?  Are the header files readable by your user?

---

### Post by adityaharish on 2013-06-03
I don't know much about compiling but  **./configure** checks for right dependencies  required in the system .

**./configure** ran successfully indicating that the dependencies required are present in the system.

How can I check whether header files are readable by user ?

---

