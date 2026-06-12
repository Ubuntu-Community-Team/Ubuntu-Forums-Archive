---
title: "where is pango for python3?"
date: 2020-11-15
forum: Programming Talk
---

### Post by Colin@oxford on 2020-11-15
I have a Python program that uses Cairo & Pango to create PDF files.  I am trying to upgrade from Python 2 to 3 and although I can find the cairo libraries, I can find no reference to pango in the repositories.  Anything that  seems to refer to it required Python2.  Do I need to add some repositories, download pango separately, or has something replaced pango for text layout?

---

### Post by norobro on 2020-11-18
Pango is in the python3-gi package. [https://packages.ubuntu.com/focal/python3-gi](https://packages.ubuntu.com/focal/python3-gi)```
[FONT=monospace][COLOR=#000000]$ python3[/COLOR]
Python 3.8.6 (default, Sep 25 2020, 09:36:53)  
[GCC 10.2.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> import gi
>>> gi.require_version("Gtk", "3.0")
>>> gi.require_version("PangoCairo", "1.0")
>>> from gi.repository import Gtk, Gdk, cairo, Pango, PangoCairo
>>> dir(Pango) 
[SIZE=1]['ANALYSIS_FLAG_CENTERED_BASELINE', 'ANALYSIS_FLAG_IS_ELLIPSIS', 'ANALYSIS_FLAG_NEED_HYPHEN', 'ATTR_INDEX_FROM_T
EXT_BEGINNING', 'Alignment', 'Analysis', 'AttrClass', 'AttrColor', 'AttrFloat', 'AttrFontDesc', 'AttrFontFeature
s', 'AttrInt', 'AttrIterator', 'AttrLanguage', 'AttrList', 'AttrShape', 'AttrSize', 'AttrString', 'AttrType', 'A
ttribute', 'BidiType', 'Color', 'Context', 'ContextClass', 'Coverage', 'CoverageLevel', 'Direction', 'ENGINE_TYP
E_LANG', 'ENGINE_TYPE_SHAPE', 'EllipsizeMode', 'Engine', 'EngineClass', 'EngineInfo', 'EngineLang', 'EngineLangC
lass', 'EngineScriptInfo', 'EngineShape', 'EngineShapeClass', 'Font', 'FontClass', 'FontDescription', 'FontFace'
, 'FontFaceClass', 'FontFamily', 'FontFamilyClass', 'FontMap', 'FontMapClass', 'FontMask', 'FontMetrics', 'Fonts
et', 'FontsetClass', 'FontsetSimple', 'FontsetSimpleClass', 'GLYPH_EMPTY', 'GLYPH_INVALID_INPUT', 'GLYPH_UNKNOWN
_FLAG', 'GlyphGeometry', 'GlyphInfo', 'GlyphItem', 'GlyphItemIter', 'GlyphString', 'GlyphVisAttr', 'Gravity', 'G
ravityHint', 'IncludedModule', 'Item', 'Language', 'Layout', 'LayoutClass', 'LayoutIter', 'LayoutLine', 'LogAttr
', 'Map', 'MapEntry', 'Matrix', 'Overline', 'RENDER_TYPE_NONE', 'Rectangle', 'RenderPart', 'Renderer', 'Renderer
Class', 'RendererPrivate', 'SCALE', 'Script', 'ScriptIter', 'ShapeFlags', 'ShowFlags', 'Stretch', 'Style', 'TabA
lign', 'TabArray', 'UNKNOWN_GLYPH_HEIGHT', 'UNKNOWN_GLYPH_WIDTH', 'Underline', 'VERSION_MIN_REQUIRED', 'Variant'
, 'Weight', 'WrapMode', '__class__', '__delattr__', '__dict__', '__dir__', '__doc__', '__eq__', '__file__', '__f
ormat__', '__ge__', '__getattr__', '__getattribute__', '__gt__', '__hash__', '__init__', '__init_subclass__', '_
_le__', '__loader__', '__lt__', '__module__', '__name__', '__ne__', '__new__', '__package__', '__path__', '__red
uce__', '__reduce_ex__', '__repr__', '__setattr__', '__sizeof__', '__spec__', '__str__', '__subclasshook__', '__
weakref__', '_introspection_module', '_namespace', '_overrides_module', '_version', 'attr_allow_breaks_new', 'at
tr_background_alpha_new', 'attr_background_new', 'attr_fallback_new', 'attr_family_new', 'attr_font_desc_new', '
attr_font_features_new', 'attr_foreground_alpha_new', 'attr_foreground_new', 'attr_gravity_hint_new', 'attr_grav
ity_new', 'attr_insert_hyphens_new', 'attr_language_new', 'attr_letter_spacing_new', 'attr_overline_color_new', 
'attr_overline_new', 'attr_rise_new', 'attr_scale_new', 'attr_shape_new', 'attr_shape_new_with_data', 'attr_show
_new', 'attr_size_new', 'attr_size_new_absolute', 'attr_stretch_new', 'attr_strikethrough_color_new', 'attr_stri
kethrough_new', 'attr_style_new', 'attr_type_get_name', 'attr_type_register', 'attr_underline_color_new', 'attr_
underline_new', 'attr_variant_new', 'attr_weight_new', 'bidi_type_for_unichar', 'break_', 'default_break', 'exte
nts_to_pixels', 'find_base_dir', 'find_paragraph_boundary', 'font_description_from_string', 'get_log_attrs', 'ge
t_mirror_char', 'gravity_get_for_matrix', 'gravity_get_for_script', 'gravity_get_for_script_and_width', 'gravity
_to_rotation', 'is_zero_width', 'itemize', 'itemize_with_base_dir', 'language_from_string', 'language_get_defaul
t', 'log2vis_get_embedding_levels', 'markup_parser_finish', 'markup_parser_new', 'parse_enum', 'parse_markup', '
parse_stretch', 'parse_style', 'parse_variant', 'parse_weight', 'quantize_line_geometry', 'read_line', 'reorder_
items', 'scan_int', 'scan_string', 'scan_word', 'script_for_unichar', 'script_get_sample_language', 'shape', 'sh
ape_full', 'shape_with_flags', 'skip_space', 'split_file_list', 'tailor_break', 'trim_string', 'unichar_directio
n', 'units_from_double', 'units_to_double', 'version', 'version_check', 'version_string'][/SIZE][/FONT]
```

---

### Post by Colin@oxford on 2020-11-19
Thanks - not at all obvious!!

---

