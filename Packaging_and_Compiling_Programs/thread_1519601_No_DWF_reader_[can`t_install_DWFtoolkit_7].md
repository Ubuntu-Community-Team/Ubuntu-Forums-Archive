---
title: "No DWF reader [can`t install DWFtoolkit 7]"
date: 2010-06-28
forum: Packaging and Compiling Programs
---

### Post by Ko$ on 2010-06-28
I know that this is not the AutoDesk forum, but I can`t find their either. I hope that someone did that already and can help me.

As far as I know there is no alternative to DWFtoolkit in order to open .DWF files in linux so I`ve downloaded their 7th version. I`m trying to build this toolkit and I have problems on the step "make install". I`m not a programmer and thats why I`ve posted it here. Maybe the errors can be easily solved by people who better understand what that means. 

From instruction I`ve read that firstly I have to build DWFcore and install it, that went fine.

Second, I need to build and install the DWFtoolkit itself.

Configure and make as far as I`ve got it went fine. But "sudo make install" says this (I`ve posted all the output, maybe it helps):

> kos@home-hp:~/tmp/DWFToolkit-7.6/develop/global/src/dwf$ sudo make install
Making install in package
make[1]: Entering directory `/home/kos/tmp/DWFToolkit-7.6/develop/global/src/dwf/package'
Making install in reader
make[2]: Entering directory `/home/kos/tmp/DWFToolkit-7.6/develop/global/src/dwf/package/reader'
make[3]: Entering directory `/home/kos/tmp/DWFToolkit-7.6/develop/global/src/dwf/package/reader'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/include/dwf/package/reader" || /bin/mkdir -p "/usr/local/include/dwf/package/reader"
 /usr/bin/install -c -m 644 ContentReader.h ContentResourceReader.h DataSectionDescriptorReader.h DuplicateAttributeFilter.h EModelSectionDescriptorReader.h EPlotSectionDescriptorReader.h GlobalSectionDescriptorReader.h ObjectDefinitionReader.h PackageManifestReader.h PackageReader.h SectionDescriptorReader.h SignatureReader.h SignatureSectionDescriptorReader.h '/usr/local/include/dwf/package/reader'
make[3]: Leaving directory `/home/kos/tmp/DWFToolkit-7.6/develop/global/src/dwf/package/reader'
make[2]: Leaving directory `/home/kos/tmp/DWFToolkit-7.6/develop/global/src/dwf/package/reader'
Making install in writer
make[2]: Entering directory `/home/kos/tmp/DWFToolkit-7.6/develop/global/src/dwf/package/writer'
Making install in extensions
make[3]: Entering directory `/home/kos/tmp/DWFToolkit-7.6/develop/global/src/dwf/package/writer/extensions'
Making install in 6.01
make[4]: Entering directory `/home/kos/tmp/DWFToolkit-7.6/develop/global/src/dwf/package/writer/extensions/6.01'
make[5]: Entering directory `/home/kos/tmp/DWFToolkit-7.6/develop/global/src/dwf/package/writer/extensions/6.01'
make[5]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/include/dwf/package/writer/extensions/6.01" || /bin/mkdir -p "/usr/local/include/dwf/package/writer/extensions/6.01"
 /usr/bin/install -c -m 644 PackageVersionExtension.h '/usr/local/include/dwf/package/writer/extensions/6.01'
make[5]: Leaving directory `/home/kos/tmp/DWFToolkit-7.6/develop/global/src/dwf/package/writer/extensions/6.01'
make[4]: Leaving directory `/home/kos/tmp/DWFToolkit-7.6/develop/global/src/dwf/package/writer/extensions/6.01'
Making install in 6.0
make[4]: Entering directory `/home/kos/tmp/DWFToolkit-7.6/develop/global/src/dwf/package/writer/extensions/6.0'
make[5]: Entering directory `/home/kos/tmp/DWFToolkit-7.6/develop/global/src/dwf/package/writer/extensions/6.0'
make[5]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/include/dwf/package/writer/extensions/6.0" || /bin/mkdir -p "/usr/local/include/dwf/package/writer/extensions/6.0"
 /usr/bin/install -c -m 644 PackageVersionExtension.h '/usr/local/include/dwf/package/writer/extensions/6.0'
make[5]: Leaving directory `/home/kos/tmp/DWFToolkit-7.6/develop/global/src/dwf/package/writer/extensions/6.0'
make[4]: Leaving directory `/home/kos/tmp/DWFToolkit-7.6/develop/global/src/dwf/package/writer/extensions/6.0'
Making install in 6.11
make[4]: Entering directory `/home/kos/tmp/DWFToolkit-7.6/develop/global/src/dwf/package/writer/extensions/6.11'
make[5]: Entering directory `/home/kos/tmp/DWFToolkit-7.6/develop/global/src/dwf/package/writer/extensions/6.11'
make[5]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/include/dwf/package/writer/extensions/6.11" || /bin/mkdir -p "/usr/local/include/dwf/package/writer/extensions/6.11"
 /usr/bin/install -c -m 644 PackageVersionExtension.h '/usr/local/include/dwf/package/writer/extensions/6.11'
make[5]: Leaving directory `/home/kos/tmp/DWFToolkit-7.6/develop/global/src/dwf/package/writer/extensions/6.11'
make[4]: Leaving directory `/home/kos/tmp/DWFToolkit-7.6/develop/global/src/dwf/package/writer/extensions/6.11'
Making install in 6.20
make[4]: Entering directory `/home/kos/tmp/DWFToolkit-7.6/develop/global/src/dwf/package/writer/extensions/6.20'
make[5]: Entering directory `/home/kos/tmp/DWFToolkit-7.6/develop/global/src/dwf/package/writer/extensions/6.20'
make[5]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/include/dwf/package/writer/extensions/6.20" || /bin/mkdir -p "/usr/local/include/dwf/package/writer/extensions/6.20"
 /usr/bin/install -c -m 644 PackageVersionExtension.h '/usr/local/include/dwf/package/writer/extensions/6.20'
make[5]: Leaving directory `/home/kos/tmp/DWFToolkit-7.6/develop/global/src/dwf/package/writer/extensions/6.20'
make[4]: Leaving directory `/home/kos/tmp/DWFToolkit-7.6/develop/global/src/dwf/package/writer/extensions/6.20'
make[4]: Entering directory `/home/kos/tmp/DWFToolkit-7.6/develop/global/src/dwf/package/writer/extensions'
make[5]: Entering directory `/home/kos/tmp/DWFToolkit-7.6/develop/global/src/dwf/package/writer/extensions'
make[5]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/include/dwf/package/writer/extensions" || /bin/mkdir -p "/usr/local/include/dwf/package/writer/extensions"
make[5]: Leaving directory `/home/kos/tmp/DWFToolkit-7.6/develop/global/src/dwf/package/writer/extensions'
make[4]: Leaving directory `/home/kos/tmp/DWFToolkit-7.6/develop/global/src/dwf/package/writer/extensions'
make[3]: Leaving directory `/home/kos/tmp/DWFToolkit-7.6/develop/global/src/dwf/package/writer/extensions'
make[3]: Entering directory `/home/kos/tmp/DWFToolkit-7.6/develop/global/src/dwf/package/writer'
make[4]: Entering directory `/home/kos/tmp/DWFToolkit-7.6/develop/global/src/dwf/package/writer'
make[4]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/include/dwf/package/writer" || /bin/mkdir -p "/usr/local/include/dwf/package/writer"
 /usr/bin/install -c -m 644 DWF6PackageVersionExtension.h DWF6PackageWriter.h DWFXPackageWriter.h PackageWriter.h DWFXPackageVersionExtension.h '/usr/local/include/dwf/package/writer'
make[4]: Leaving directory `/home/kos/tmp/DWFToolkit-7.6/develop/global/src/dwf/package/writer'
make[3]: Leaving directory `/home/kos/tmp/DWFToolkit-7.6/develop/global/src/dwf/package/writer'
make[2]: Leaving directory `/home/kos/tmp/DWFToolkit-7.6/develop/global/src/dwf/package/writer'
Making install in utility
make[2]: Entering directory `/home/kos/tmp/DWFToolkit-7.6/develop/global/src/dwf/package/utility'
make[3]: Entering directory `/home/kos/tmp/DWFToolkit-7.6/develop/global/src/dwf/package/utility'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/include/dwf/package/utility" || /bin/mkdir -p "/usr/local/include/dwf/package/utility"
 /usr/bin/install -c -m 644 DefinedObjectContainer.h DWFPackageFileDescriptor.h PropertyContainer.h ResourceContainer.h '/usr/local/include/dwf/package/utility'
make[3]: Leaving directory `/home/kos/tmp/DWFToolkit-7.6/develop/global/src/dwf/package/utility'
make[2]: Leaving directory `/home/kos/tmp/DWFToolkit-7.6/develop/global/src/dwf/package/utility'
make[2]: Entering directory `/home/kos/tmp/DWFToolkit-7.6/develop/global/src/dwf/package'
make[3]: Entering directory `/home/kos/tmp/DWFToolkit-7.6/develop/global/src/dwf/package'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/include/dwf/package" || /bin/mkdir -p "/usr/local/include/dwf/package"
 /usr/bin/install -c -m 644 Bookmark.h Class.h Constants.h Content.h ContentElement.h ContentManager.h CoordinateSystem.h CustomSection.h DataSection.h DefinedObject.h Dependency.h DwfResult.h EModelSection.h Entity.h EPlotSection.h Feature.h FontResource.h GlobalSection.h GraphicResource.h Group.h Instance.h Interface.h Manifest.h Object.h ObjectDefinition.h ObjectDefinitionResource.h Paper.h Property.h PropertySet.h Renderable.h Resource.h Section.h SectionBuilder.h SectionContentResource.h Signature.h SignatureRequest.h SignatureSection.h SignatureResource.h Source.h Units.h '/usr/local/include/dwf/package'
 /usr/bin/install -c -m 644 X509.h XML.h '/usr/local/include/dwf/package'
make[3]: Leaving directory `/home/kos/tmp/DWFToolkit-7.6/develop/global/src/dwf/package'
make[2]: Leaving directory `/home/kos/tmp/DWFToolkit-7.6/develop/global/src/dwf/package'
make[1]: Leaving directory `/home/kos/tmp/DWFToolkit-7.6/develop/global/src/dwf/package'
Making install in whiptk
make[1]: Entering directory `/home/kos/tmp/DWFToolkit-7.6/develop/global/src/dwf/whiptk'
make[2]: Entering directory `/home/kos/tmp/DWFToolkit-7.6/develop/global/src/dwf/whiptk'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/include/dwf/whiptk" || /bin/mkdir -p "/usr/local/include/dwf/whiptk"
 /usr/bin/install -c -m 644 allclass.h attribute.h attribute_url.h backgrnd.h blockref.h blockref_defs.h blockref_list.h code_page.h color.h colormap.h compdata.h contour_set.h contrastcolor.h convert_utf.h dashpat.h delineate.h directory.h dpat_list.h drawable.h dwfhead.h dwginfo.h ellipse.h embed.h embedded_font.h endofdwf.h fifo.h file.h file_stats.h fileext.h filetime.h fill.h fillpat.h font.h font_extension.h font_options.h gouraud_pointset.h gouraud_polyline.h gouraud_polytri.h group_begin.h group_end.h '/usr/local/include/dwf/whiptk'
 /usr/bin/install -c -m 644 guid_list.h heuristics.h image.h informational.h inked_area.h layer.h layer_list.h linepat.h linestyle.h list.h logical_box.h logical_point.h lweight.h lz77comp.h lz77decp.h lzdefs.h macro_definition.h macro_draw.h macro_scale.h macro_index.h marksize.h marksymb.h matrix.h merge_control.h named_view.h named_view_list.h object.h object_node.h object_node_list.h object_stream.h opcode.h opcode_defs.h origin.h overpost.h palette.h pattern_scale.h pch.h penpat.h penpat_options.h plot_optimized.h '/usr/local/include/dwf/whiptk'
 /usr/bin/install -c -m 644 plotinfo.h pnggroup4image.h point.h pointset.h polygon.h polyline.h polymark.h polytri.h preload.h projection.h rendition.h rendopts.h resource.h rgb.h signdata.h text.h text_background.h text_options.h text_halign.h text_valign.h timestamp.h transform.h trusted_font_list.h typedefs_defines.h units.h unknown.h url.h url_list.h userdata.h usrfillpat.h usrhatchpat.h view.h viewport.h viewport_options.h visible.h whip_toolkit.h whipcore.h whiperrs.h wtstring.h wversion.h '/usr/local/include/dwf/whiptk'
 /usr/bin/install -c -m 644 wendian.h class_factory.h w2d_class_factory.h '/usr/local/include/dwf/whiptk'
make[2]: Leaving directory `/home/kos/tmp/DWFToolkit-7.6/develop/global/src/dwf/whiptk'
make[1]: Leaving directory `/home/kos/tmp/DWFToolkit-7.6/develop/global/src/dwf/whiptk'
Making install in XAML
make[1]: Entering directory `/home/kos/tmp/DWFToolkit-7.6/develop/global/src/dwf/XAML'
make[2]: Entering directory `/home/kos/tmp/DWFToolkit-7.6/develop/global/src/dwf/XAML'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/include/dwf/XAML" || /bin/mkdir -p "/usr/local/include/dwf/XAML"
 /usr/bin/install -c -m 644 allclass.h MemoryBuffer.h OpcResourceMaterializer.h OpcResourceSerializer.h pch.h resource.h XamlArcSegment.h XamlAttribute.h XamlAttribute_Url.h XamlBrushes.h XamlCanvas.h XamlClassFactory.h XamlCode_Page.h XamlColor.h XamlColorMap.h XamlContour_Set.h XamlContrastColor.h XamlCore.h XamlDashPattern.h XamlDelineate.h XamlDrawable.h XamlDrawableAttributes.h XamlDwfHeader.h XamlEllipse.h XamlEmbed.h XamlEmbeddedFont.h XamlEndOfDwf.h XamlFile.h XamlFill.h XamlFillPattern.h XamlFontExtension.h XamlFont.h XamlFontExtension.h XamlFontUtil.h XamlGlyphs.h XamlGouraud_Polyline.h XamlGouraud_Polytriangle.h XamlGraphicsObject.h XamlImage.h XamlLayer.h '/usr/local/include/dwf/XAML'
/usr/bin/install: will not overwrite just-created `/usr/local/include/dwf/XAML/XamlFontExtension.h' with `XamlFontExtension.h'
make[2]: *** [install-XAML_includeHEADERS] Error 1
make[2]: Leaving directory `/home/kos/tmp/DWFToolkit-7.6/develop/global/src/dwf/XAML'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/kos/tmp/DWFToolkit-7.6/develop/global/src/dwf/XAML'
make: *** [install-recursive] Error 1
kos@home-hp:~/tmp/DWFToolkit-7.6/develop/global/src/dwf$ 


So the question is can it be solved without developers of autodesk?

---

### Post by SevenMachines on 2010-06-28
the install command includes two mentions of XamlFontExtension.h, you need to have only one. i dont know about dwf but i'm guessing this is an autogenerated makefile? either way you need to remove the duplicate arguments to install

---

