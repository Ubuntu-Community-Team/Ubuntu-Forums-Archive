---
title: "Java Graphics Unnecessary Repainting"
date: 2010-07-11
forum: Programming Talk
---

### Post by SNYP40A1 on 2010-07-11
I am using JFreeChart to draw graphics in Java.  I find that the draw function is called several times back to back while I expect that it should only be called once.  I want to figure out what's triggering the repaint() or update() calls.  I put in a Thread.dumpStack() at the place of redraw, but it only tells me that the repaint call originated from the Swing EventDispatch thread.  How do I determine what actually notified the Swing Dispatcher to repaint the plot?  Is there a Swing trace debug method for this?

[PHP]
java.lang.Exception: Stack trace
	at java.lang.Thread.dumpStack(Thread.java:1206)
	at org.jfree.chart.renderer.xy.XYBarRenderer.drawItems(XYBarRenderer.java:1343)
	at org.jfree.chart.plot.XYPlot.render(XYPlot.java:3738)
	at org.jfree.chart.plot.XYPlot.draw(XYPlot.java:3311)
	at org.jfree.chart.JFreeChart.draw(JFreeChart.java:1234)
	at org.jfree.chart.ChartPanel.paintComponent(ChartPanel.java:1663)
	at javax.swing.JComponent.paint(JComponent.java:1029)
	at javax.swing.JComponent.paintToOffscreen(JComponent.java:5124)
	at javax.swing.RepaintManager$PaintManager.paintDoubleBuffered(RepaintManager.java:1479)
	at javax.swing.RepaintManager$PaintManager.paint(RepaintManager.java:1410)
	at javax.swing.BufferStrategyPaintManager.paint(BufferStrategyPaintManager.java:294)
	at javax.swing.RepaintManager.paint(RepaintManager.java:1224)
	at javax.swing.JComponent._paintImmediately(JComponent.java:5072)
	at javax.swing.JComponent.paintImmediately(JComponent.java:4882)
	at javax.swing.RepaintManager.paintDirtyRegions(RepaintManager.java:785)
	at javax.swing.RepaintManager.paintDirtyRegions(RepaintManager.java:713)
	at javax.swing.RepaintManager.seqPaintDirtyRegions(RepaintManager.java:693)
	at javax.swing.SystemEventQueueUtilities$ComponentWorkRequest.run(SystemEventQueueUtilities.java:125)
	at java.awt.event.InvocationEvent.dispatch(InvocationEvent.java:209)
	at java.awt.EventQueue.dispatchEvent(EventQueue.java:597)
	at java.awt.EventDispatchThread.pumpOneEventForFilters(EventDispatchThread.java:269)
	at java.awt.EventDispatchThread.pumpEventsForFilter(EventDispatchThread.java:184)
	at java.awt.EventDispatchThread.pumpEventsForHierarchy(EventDispatchThread.java:174)
	at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:169)
	at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:161)
	at java.awt.EventDispatchThread.run(EventDispatchThread.java:122)
[/PHP]

---

