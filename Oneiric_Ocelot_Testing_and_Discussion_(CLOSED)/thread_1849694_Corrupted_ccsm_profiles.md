---
title: "Corrupted ccsm profiles"
date: 2011-09-25
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by effenberg0x0 on 2011-09-25
This is new to me so I thought I should ask in the forums before starting to mess with the system more seriously to find a workaround.

All of a sudden I have "Default" plus 2 corrupted profiles at CCSM. See screenshot. If I try to select any of these profiles, so that I can press the "minus button" to delete them, unity crashes. 

The backend is selected to GConf, as you can see in the screenshot. However, looking at gconf-editor, I have Default and Unity as the only available compizconfig profiles.

Trying to add a new profile at ccsm also crashes unity. Trying to save current compiz settings to default crashes unity too.

Is anyone else seeing anything like this?

Thanks,
Effenberg

**EDIT:**

Managed to remove the corrupted profiles by purging / reinstalling compizconfig-backend-gconf.
Still, I cannot use ccsm to save changes to default or create a new profile. Although sort of useless, here's the segfault:

```

[  235.731192] compiz[2427]: segfault at f8 ip 00007f7e9f4652ae sp 00007fffb05457d0 error 4 in libsigc-2.0.so.0.0.0[7f7e9f463000+4000]
[  611.444881] compiz[2983]: segfault at 171 ip 0000000000000171 sp 00007fff1bfa8fb8 error 14 in compiz[400000+74000]
[  791.921850] compiz[6797]: segfault at 150 ip 00007f0b2af28e86 sp 00007fffcedce040 error 4 in libunityshell.so[7f0b2add0000+20c000]
[  864.059180] compiz[7461]: segfault at 0 ip 00000000409f9ed3 sp 00007fffacb44b18 error 4 in glOfQ9P1 (deleted)[409f8000+2000]
[ 1229.509355] compiz[7919]: segfault at 0 ip 0000000040777ed3 sp 00007fff8fa00b88 error 4 in glh2N8hu (deleted)[40776000+2000]
[ 4010.365265] compiz[7977]: segfault at f8 ip 00007f3b0eaac2ae sp 00007fffc7b400b0 error 4 in libsigc-2.0.so.0.0.0[7f3b0eaaa000+4000]
[ 4016.042016] compiz[8345]: segfault at f8 ip 00007ff78e04f2ae sp 00007fff947ab320 error 4 in libsigc-2.0.so.0.0.0[7ff78e04d000+4000]
[ 4227.547592] compiz[8434]: segfault at 118 ip 00007f15e70352f4 sp 00007fff52255c10 error 4 in libnvidia-glcore.so.280.13[7f15e5ff9000+15f4000]
[ 4424.399059] compiz[8770]: segfault at f8 ip 00007fbf3c0de2ae sp 00007ffffe3a1490 error 4 in libsigc-2.0.so.0.0.0[7fbf3c0dc000+4000]
[ 4601.653106] compiz[9084]: segfault at f8 ip 00007fcd6bff82ae sp 00007fffdedb6c80 error 4 in libsigc-2.0.so.0.0.0[7fcd6bff6000+4000]

```

---

### Post by mc4man on 2011-09-25
I've got default plus 1 add. that I didn't create - screen, 2 day old install

Atm ccsm is quite unpredictable & possibly messy. (or nothing bad may happen at all except those 'wait out resets'

(I just maintain some gconf commands in bash to restore my  settings when the inevitable happens

ccsm almost always produces [a crash]("https://bugs.launchpad.net/ubuntu/+source/compizconfig-settings-manager/+bug/832458"), though most times unnoticeable unless you get a pop up. Sometimes it seems that can lead to a compiz crash of varying sorts, most times not
I figure another 6 months or so for compiz..

---

### Post by effenberg0x0 on 2011-09-25
Hi mc4man

Oh well, so it is the usual behavior right now. No need to report it I think.

Thanks,
Effenberg

---

### Post by mc4man on 2011-09-25
Whether that/those profiles are 'normal' don't really know, this was the 1st. time i'd opened preferences on this install. - beta 2
(& just opening preferences locked up/crashed compiz, after resetting everything then opening pref.'s went fine..

I think I'll probably do a fresh install when unity-4.18 releases & is on the daily

Edit: - booted to a live session, installed ccsm, & see 2 extra profiles - trying to load one produces  - 
> GConf Error: Bad key or directory name: "/apps/compizconfig-1/profiles/&#65533;&#65533;)	": '\310' is not an ASCII character and thus isn't allowed in key names


Some it seems par for the current course

---

### Post by effenberg0x0 on 2011-09-25
Exactly what I see here. Go to that key with gconf-editor. In my case there's nothing corrupted there. The Compiz Gconf Backend is looking for something that isn't there.

Regards,
Effenberg

---

### Post by ventrical on 2011-09-25
> **mc4man said:**
> Whether that/those profiles are 'normal' don't really know, this was the 1st. time i'd opened preferences on this install. - beta 2
(& just opening preferences locked up/crashed compiz, after resetting everything then opening pref.'s went fine..

I think I'll probably do a fresh install when unity-4.18 releases & is on the daily

Edit: - booted to a live session, installed ccsm, & see 2 extra profiles - trying to load one produces  - 


Some it seems par for the current course 


Yes .. happened here too with the preferences. I also noticed that compiz will crash if you kill a program (totem) in processes. I noticed that if I proceeded in a slow an patient manner that compiz is very stable but if I tried to force something or close somthing too fast (?) then it would crash. Otherwise the wait-reset is not all that bad for now.

---

### Post by effenberg0x0 on 2011-09-25
Have you ever had any success with the flatfile backend? It always crashed for me (save, create, export, import, whatever).

Regards
Effenberg

---

### Post by ventrical on 2011-09-25
I can't take a screen shot of those files - but I got this screen shot:
So what kind of file should I import??any examples??

---

### Post by ventrical on 2011-09-25
I just created (exported) this current profile:

```

[mag]
s0_initiate = <Super>m
s0_zoom_in_button = <Shift><Super>Button4
s0_zoom_out_button = <Shift><Super>Button5
s0_mode = 0
s0_zoom_factor = 2.000000
s0_speed = 1.500000
s0_timestep = 1.200000
s0_keep_screen = true
s0_box_width = 300
s0_box_height = 200
s0_border = 2
s0_box_color = #000000ff
s0_overlay = Gnome/overlay.png
s0_mask = Gnome/mask.png
s0_x_offset = 155
s0_y_offset = 155
s0_radius = 200

[kdecompat]
s0_plasma_thumbnails = true
s0_present_windows = true
s0_window_blur = true
s0_sliding_popups = true
s0_slide_in_duration = 250
s0_slide_out_duration = 250

[cube]
s0_unfold_key = <Control><Alt>Down
s0_mipmap = true
s0_multioutput_mode = 0
s0_in = false
s0_acceleration = 4.000000
s0_speed = 1.500000
s0_timestep = 1.200000
s0_top_color = #cdbe70ff
s0_bottom_color = #cdbe70ff
s0_skydome = false
s0_skydome_image = 
s0_skydome_animated = false
s0_skydome_gradient_start_color = #0db1fdff
s0_skydome_gradient_end_color = #feffc7ff
s0_active_opacity = 100.000000
s0_inactive_opacity = 100.000000
s0_transparent_manual_only = true

[put]
s0_put_viewport_1_key = Disabled
s0_put_viewport_2_key = Disabled
s0_put_viewport_3_key = Disabled
s0_put_viewport_4_key = Disabled
s0_put_viewport_5_key = Disabled
s0_put_viewport_6_key = Disabled
s0_put_viewport_7_key = Disabled
s0_put_viewport_8_key = Disabled
s0_put_viewport_9_key = Disabled
s0_put_viewport_10_key = Disabled
s0_put_viewport_11_key = Disabled
s0_put_viewport_12_key = Disabled
s0_put_viewport_left_key = Disabled
s0_put_viewport_right_key = Disabled
s0_put_viewport_up_key = Disabled
s0_put_viewport_down_key = Disabled
s0_put_center_key = <Super>KP_Begin
s0_put_center_button = Disabled
s0_put_left_key = <Super>KP_Left
s0_put_left_button = Disabled
s0_put_right_key = <Super>KP_Right
s0_put_right_button = Disabled
s0_put_top_key = <Super>KP_Up
s0_put_top_button = Disabled
s0_put_bottom_key = <Super>KP_Down
s0_put_bottom_button = Disabled
s0_put_topleft_key = <Super>KP_Home
s0_put_topleft_button = Disabled
s0_put_topright_key = <Super>KP_Prior
s0_put_topright_button = Disabled
s0_put_bottomleft_key = <Super>KP_End
s0_put_bottomleft_button = Disabled
s0_put_bottomright_key = <Super>KP_Next
s0_put_bottomright_button = Disabled
s0_put_empty_center_key = Disabled
s0_put_empty_center_button = Disabled
s0_put_empty_left_key = Disabled
s0_put_empty_left_button = Disabled
s0_put_empty_right_key = Disabled
s0_put_empty_right_button = Disabled
s0_put_empty_top_key = Disabled
s0_put_empty_top_button = Disabled
s0_put_empty_bottom_key = Disabled
s0_put_empty_bottom_button = Disabled
s0_put_empty_topleft_key = Disabled
s0_put_empty_topleft_button = Disabled
s0_put_empty_topright_key = Disabled
s0_put_empty_topright_button = Disabled
s0_put_empty_bottomleft_key = Disabled
s0_put_empty_bottomleft_button = Disabled
s0_put_empty_bottomright_key = Disabled
s0_put_empty_bottomright_button = Disabled
s0_put_restore_key = <Super>KP_Insert
s0_put_restore_button = Disabled
s0_put_pointer_key = <Super>z
s0_put_pointer_button = Disabled
s0_put_next_output_key = Disabled
s0_put_next_output_button = Disabled
s0_pad_left = 0
s0_pad_right = 0
s0_pad_top = 0
s0_pad_bottom = 0
s0_unfocus_window = false
s0_window_center = false
s0_avoid_offscreen = false
s0_speed = 2.500000
s0_timestep = 0.500000

[wobbly]
s0_snap_key = <Shift>
s0_snap_inverted = false
s0_shiver = false
s0_friction = 3.000000
s0_spring_k = 8.000000
s0_grid_resolution = 8
s0_min_grid_size = 8
s0_map_effect = 0
s0_focus_effect = 0
s0_map_window_match = Splash | DropdownMenu | PopupMenu | Tooltip | Notification | Combo | Dnd | Unknown
s0_focus_window_match = 
s0_grab_window_match = 
s0_move_window_match = Toolbar | Menu | Utility | Dialog | Normal | Unknown
s0_maximize_effect = true

[imgjpeg]
s0_quality = 80

[blur]
s0_pulse = false
s0_blur_speed = 3.500000
s0_focus_blur_match = toolbar | menu | utility | normal | dialog | modaldialog
s0_focus_blur = false
s0_alpha_blur_match = 
s0_alpha_blur = true
s0_filter = 0
s0_gaussian_radius = 3
s0_gaussian_strength = 1.000000
s0_mipmap_lod = 2.500000
s0_saturation = 100
s0_occlusion = true
s0_independent_tex = false

[gnomecompat]
s0_main_menu_key = <Alt>F1
s0_run_key = <Alt>F2
s0_command_screenshot = gnome-screenshot
s0_run_command_screenshot_key = Print
s0_command_window_screenshot = gnome-screenshot --window
s0_run_command_window_screenshot_key = <Alt>Print
s0_command_terminal = gnome-terminal
s0_run_command_terminal_key = <Control><Alt>T

[vpswitch]
s0_begin_key = Disabled
s0_switch_to_1_key = Disabled
s0_switch_to_2_key = Disabled
s0_switch_to_3_key = Disabled
s0_switch_to_4_key = Disabled
s0_switch_to_5_key = Disabled
s0_switch_to_6_key = Disabled
s0_switch_to_7_key = Disabled
s0_switch_to_8_key = Disabled
s0_switch_to_9_key = Disabled
s0_switch_to_10_key = Disabled
s0_switch_to_11_key = Disabled
s0_switch_to_12_key = Disabled
s0_left_button = Disabled
s0_right_button = Disabled
s0_up_button = Disabled
s0_down_button = Disabled
s0_next_button = Disabled
s0_prev_button = Disabled
s0_initiate_button = Button2
s0_init_plugin = rotate
s0_init_action = initiate_button

[unitymtgrabhandles]
s0_toggle_handles_key = Disabled
s0_show_handles_key = Disabled
s0_hide_handles_key = Disabled
s0_fade_duration = 150

[ezoom]
s0_zoom_in_button = Disabled
s0_zoom_in_key = Disabled
s0_zoom_out_button = Disabled
s0_zoom_out_key = Disabled
s0_zoom_box_button = Disabled
s0_center_mouse_key = Disabled
s0_zoom_specific_1_key = Disabled
s0_zoom_spec1 = 1.000000
s0_zoom_specific_2_key = Disabled
s0_zoom_spec2 = 0.500000
s0_zoom_specific_3_key = Disabled
s0_zoom_spec3 = 0.200000
s0_spec_target_focus = true
s0_lock_zoom_key = Disabled
s0_pan_left_key = Disabled
s0_pan_right_key = Disabled
s0_pan_up_key = Disabled
s0_pan_down_key = Disabled
s0_fit_to_zoom_key = Disabled
s0_fit_to_window_key = Disabled
s0_zoom_factor = 1.150000
s0_minimum_zoom = 0.125000
s0_zoom_mode = 0
s0_scale_mouse = true
s0_scale_mouse_dynamic = true
s0_scale_mouse_static = 0.200000
s0_hide_original_mouse = true
s0_restrain_mouse = false
s0_restrain_margin = 5
s0_pan_factor = 0.100000
s0_follow_focus = true
s0_focus_fit_window = false
s0_autoscale_min = 0.250000
s0_always_focus_fit_window = false
s0_follow_focus_delay = 0
s0_speed = 25.000000
s0_timestep = 1.200000

[water]
s0_initiate_key = <Control><Super>
s0_toggle_rain_key = <Shift>F9
s0_toggle_wiper_key = <Shift>F8
s0_offset_scale = 1.000000
s0_rain_delay = 250
s0_title_wave = false

[decor]
s0_shadow_radius = 15.000000
s0_shadow_opacity = 0.500000
s0_shadow_color = #00000000
s0_shadow_x_offset = 1
s0_shadow_y_offset = 5
s0_command = /usr/bin/compiz-decorator
s0_mipmap = false
s0_decoration_match = any
s0_shadow_match = any

[detection]
s0_detect_bad_pci = true
s0_detect_bad_drivers = true

[session]
s0_save_legacy = false
s0_ignore_match = 

[move]
s0_initiate_button = <Alt>Button1
s0_initiate_key = <Alt>F7
s0_opacity = 100
s0_constrain_y = true
s0_snapoff_maximized = true
s0_lazy_positioning = true

[screenshot]
s0_initiate_button = <Super>Button1
s0_directory = 
s0_launch_app = 

[snap]
s0_avoid_snap = 0;
s0_snap_type = 0;
s0_edges_categories = 0;
s0_resistance_distance = 30
s0_attraction_distance = 20

[wall]
s0_show_switcher = true
s0_miniscreen = true
s0_preview_timeout = 0.200000
s0_preview_scale = 130
s0_edge_radius = 5
s0_border_width = 7
s0_outline_color = #ffffff32
s0_background_gradient_base_color = #00000064
s0_background_gradient_highlight_color = #00000064
s0_background_gradient_shadow_color = #00000064
s0_thumb_gradient_base_color = #55555532
s0_thumb_gradient_highlight_color = #55555532
s0_thumb_highlight_gradient_base_color = #ffffffff
s0_thumb_highlight_gradient_shadow_color = #dfdfdfff
s0_arrow_base_color = #e6e6e6d9
s0_arrow_shadow_color = #dcdcdcd9
s0_allow_wraparound = false
s0_slide_duration = 0.300000
s0_no_slide_match = type=Dock | type=Desktop | state=Sticky
s0_left_key = <Control><Alt>Left
s0_left_button = Disabled
s0_right_key = <Control><Alt>Right
s0_right_button = Disabled
s0_up_key = <Control><Alt>Up
s0_up_button = Disabled
s0_down_key = <Control><Alt>Down
s0_down_button = Disabled
s0_next_key = Disabled
s0_next_button = Disabled
s0_prev_key = Disabled
s0_prev_button = Disabled
s0_left_window_key = <Shift><Control><Alt>Left
s0_right_window_key = <Shift><Control><Alt>Right
s0_up_window_key = <Shift><Control><Alt>Up
s0_down_window_key = <Shift><Control><Alt>Down
s0_flip_left_edge = 
s0_flip_right_edge = Right
s0_flip_up_edge = Top
s0_flip_down_edge = Bottom
s0_mmmode = 0
s0_edgeflip_pointer = false
s0_edgeflip_move = false
s0_edgeflip_dnd = false

[expo]
s0_expo_key = <Super>s
s0_expo_button = Disabled
s0_expo_edge = 
s0_double_click_time = 500
s0_dnd_button = Button1
s0_exit_button = Button3
s0_next_vp_button = Button5
s0_prev_vp_button = Button4
s0_zoom_time = 0.300000
s0_expo_immediate_move = false
s0_expo_animation = 0
s0_deform = 0
s0_x_offset = 64
s0_y_offset = 24
s0_distance = 0.005000
s0_vp_distance = 0.200000
s0_aspect_ratio = 1.000000
s0_curve = 0.500000
s0_hide_docks = false
s0_mipmaps = false
s0_multioutput_mode = 0
s0_vp_brightness = 40.000000
s0_vp_saturation = 40.000000
s0_selected_color = #fb8b00ff
s0_reflection = false
s0_ground_color1 = #b3b3b3cc
s0_ground_color2 = #b3b3b300
s0_ground_size = 0.500000
s0_scale_factor = 1.000000

[composite]
s0_slow_animations_key = Disabled
s0_detect_refresh_rate = true
s0_refresh_rate = 50
s0_unredirect_fullscreen_windows = false
s0_force_independent_output_painting = false

[opacify]
s0_toggle_key = <Super>o
s0_toggle_reset = true
s0_timeout = 700
s0_init_toggle = true
s0_only_if_block = false
s0_focus_instant = false
s0_no_delay_change = false
s0_window_match = Normal | Dialog | ModalDialog | Utility | Toolbar | Fullscreen
s0_active_opacity = 100
s0_passive_opacity = 10

[scaleaddon]
s0_close_key = Disabled
s0_close_button = Button2
s0_pull_key = Disabled
s0_pull_button = Disabled
s0_zoom_key = Disabled
s0_zoom_button = Button3
s0_window_title = 1
s0_title_bold = false
s0_title_size = 13
s0_border_size = 3
s0_font_color = #ffffffff
s0_back_color = #00000099
s0_window_highlight = false
s0_highlight_color = #ffffff96
s0_layout_mode = 0
s0_natural_precision = 2.000000
s0_constrain_pull_to_screen = true
s0_exit_after_pull = false

[obs]
s0_opacity_increase_key = Disabled
s0_opacity_increase_button = <Alt>Button4
s0_opacity_decrease_key = Disabled
s0_opacity_decrease_button = <Alt>Button5
s0_opacity_step = 5
s0_opacity_matches = 
s0_opacity_values = 90;
s0_brightness_increase_key = Disabled
s0_brightness_increase_button = Disabled
s0_brightness_decrease_key = Disabled
s0_brightness_decrease_button = Disabled
s0_brightness_step = 5
s0_brightness_matches = 
s0_brightness_values = 90;
s0_saturation_increase_key = Disabled
s0_saturation_increase_button = Disabled
s0_saturation_decrease_key = Disabled
s0_saturation_decrease_button = Disabled
s0_saturation_step = 5
s0_saturation_matches = 
s0_saturation_values = 90;

[shift]
s0_initiate_key = <Shift><Super>s
s0_initiate_button = Disabled
s0_initiate_edge = 
s0_initiate_all_key = Disabled
s0_initiate_all_button = Disabled
s0_initiate_all_edge = 
s0_terminate_button = Button3
s0_next_key = <Super>Tab
s0_next_button = Disabled
s0_prev_key = <Shift><Super>Tab
s0_prev_button = Disabled
s0_next_all_key = <Alt><Super>Tab
s0_next_all_button = Disabled
s0_prev_all_key = <Shift><Alt><Super>Tab
s0_prev_all_button = Disabled
s0_next_group_key = Disabled
s0_next_group_button = Disabled
s0_prev_group_key = Disabled
s0_prev_group_button = Disabled
s0_speed = 1.500000
s0_shift_speed = 1.000000
s0_timestep = 1.200000
s0_window_match = Normal | Dialog | ModalDialog | Utility | Unknown
s0_minimized = true
s0_mouse_speed = 10.000000
s0_click_duration = 500
s0_mode = 0
s0_size = 50
s0_background_intensity = 0.500000
s0_hide_all = false
s0_reflection = true
s0_ground_color1 = #b3b3b3cc
s0_ground_color2 = #b3b3b300
s0_ground_size = 0.500000
s0_intensity = 0.400000
s0_flip_rotation = 30
s0_cover_offset = 0.000000
s0_cover_angle = 60.000000
s0_cover_extra_space = 1.000000
s0_cover_max_visible_windows = 10
s0_overlay_icon = 1
s0_mipmaps = false
s0_multioutput_mode = 0
s0_window_title = true
s0_title_font_bold = false
s0_title_font_size = 16
s0_title_back_color = #00000099
s0_title_font_color = #ffffffff
s0_title_text_placement = 2

[bailer]
s0_fatal_fallback_mode = 2
s0_custom_fallback_window_manager = 
s0_custom_alternative_shell = 
s0_poor_performance_fallback = 0
s0_bad_performance_threshold = 50
s0_bad_plugins = 

[debugspew]
s0_spew_key = Disabled
s0_spew_on_fatal = true

[neg]
s0_window_toggle_key = <Super>n
s0_screen_toggle_key = <Super>m
s0_neg_match = any
s0_exclude_match = type=Desktop
s0_neg_decorations = false

[switcher]
s0_next_button = Disabled
s0_next_key = <Alt>Tab
s0_prev_button = Disabled
s0_prev_key = <Shift><Alt>Tab
s0_next_all_button = Disabled
s0_next_all_key = <Control><Alt>Tab
s0_prev_all_button = Disabled
s0_prev_all_key = <Shift><Control><Alt>Tab
s0_next_no_popup_button = Disabled
s0_next_no_popup_key = Disabled
s0_prev_no_popup_button = Disabled
s0_prev_no_popup_key = Disabled
s0_next_panel_button = Disabled
s0_next_panel_key = Disabled
s0_prev_panel_button = Disabled
s0_prev_panel_key = Disabled
s0_speed = 1.500000
s0_timestep = 1.200000
s0_window_match = Toolbar | Utility | Dialog | Normal | Unknown
s0_mipmap = true
s0_saturation = 100
s0_brightness = 65
s0_opacity = 40
s0_focus_on_switch = false
s0_bring_to_front = true
s0_zoom = 1.000000
s0_icon = true
s0_icon_only = false
s0_minimized = true
s0_auto_rotate = false

[scale]
s0_spacing = 68
s0_speed = 2.400000
s0_timestep = 0.100000
s0_darken_back = true
s0_opacity = 100
s0_overlay_icon = 0
s0_window_match = Toolbar | Utility | Dialog | Normal | Unknown
s0_hover_time = 750
s0_dnd_distance = 6
s0_multioutput_mode = 0
s0_key_bindings_toggle = true
s0_button_bindings_toggle = false
s0_initiate_edge = 
s0_initiate_key = <Shift><Alt>Up
s0_initiate_button = Disabled
s0_initiate_all_edge = 
s0_initiate_all_button = Disabled
s0_initiate_all_key = <Super>w
s0_initiate_group_edge = 
s0_initiate_group_button = Disabled
s0_initiate_group_key = Disabled
s0_initiate_output_edge = 
s0_initiate_output_button = Disabled
s0_initiate_output_key = Disabled
s0_show_desktop = false

[resize]
s0_initiate_button = <Alt>Button2
s0_initiate_key = <Alt>F8
s0_mode = 2
s0_resize_from_center = false
s0_border_color = #fb8b009f
s0_fill_color = #fb8b0019
s0_normal_match = 
s0_outline_match = 
s0_rectangle_match = 
s0_stretch_match = 
s0_resize_from_center_match = 
s0_outline_modifier = 
s0_rectangle_modifier = 
s0_stretch_modifier = 
s0_centered_modifier = 0;

[opengl]
s0_texture_filter = 1
s0_lighting = false
s0_sync_to_vblank = true
s0_texture_compression = false

[unityshell]
s0_launcher_reveal_edge = Left
s0_launcher_reveal_edge_timeout = 150
s0_launcher_hide_mode = 2
s0_show_launcher = <Super>
s0_keyboard_focus = <Alt>F1
s0_execute_command = <Alt>F2
s0_panel_first_menu = F10
s0_alt_tab_timeout = true
s0_alt_tab_forward = Disabled
s0_alt_tab_prev = Disabled
s0_alt_tab_right = <Alt>Right
s0_alt_tab_left = <Alt>Left
s0_alt_tab_detail_start = <Alt>Down
s0_alt_tab_detail_stop = <Alt>Up
s0_alt_tab_next_window = Disabled
s0_alt_tab_prev_window = Disabled
s0_show_minimized_windows = false
s0_backlight_mode = 0
s0_launch_animation = 1
s0_urgent_animation = 2
s0_panel_opacity = 1.000000
s0_launcher_opacity = 0.666700
s0_icon_size = 48
s0_autohide_animation = 3
s0_dash_blur_experimental = 2
s0_automaximize_value = 75
s0_devices_option = 1

[rotate]
s0_edge_flip_pointer = false
s0_edge_flip_window = true
s0_edge_flip_dnd = true
s0_raise_on_rotate = false
s0_invert_y = false
s0_snap_top = false
s0_snap_bottom = false
s0_zoom = 1.000000
s0_flip_time = 350
s0_sensitivity = 1.000000
s0_acceleration = 4.000000
s0_speed = 2.000000
s0_timestep = 1.000000
s0_initiate_button = <Control><Alt>Button1
s0_rotate_left_key = <Control><Alt>Left
s0_rotate_left_button = Disabled
s0_rotate_right_key = <Control><Alt>Right
s0_rotate_right_button = Disabled
s0_rotate_left_window_key = <Shift><Control><Alt>Left
s0_rotate_left_window_button = Disabled
s0_rotate_right_window_key = <Shift><Control><Alt>Right
s0_rotate_right_window_button = Disabled
s0_rotate_to_key = Disabled
s0_rotate_window_key = Disabled
s0_rotate_flip_left_edge = 
s0_rotate_flip_right_edge = Right
s0_rotate_to_1_key = Disabled
s0_rotate_to_2_key = Disabled
s0_rotate_to_3_key = Disabled
s0_rotate_to_4_key = Disabled
s0_rotate_to_5_key = Disabled
s0_rotate_to_6_key = Disabled
s0_rotate_to_7_key = Disabled
s0_rotate_to_8_key = Disabled
s0_rotate_to_9_key = Disabled
s0_rotate_to_10_key = Disabled
s0_rotate_to_11_key = Disabled
s0_rotate_to_12_key = Disabled
s0_rotate_to_1_window_key = Disabled
s0_rotate_to_2_window_key = Disabled
s0_rotate_to_3_window_key = Disabled
s0_rotate_to_4_window_key = Disabled
s0_rotate_to_5_window_key = Disabled
s0_rotate_to_6_window_key = Disabled
s0_rotate_to_7_window_key = Disabled
s0_rotate_to_8_window_key = Disabled
s0_rotate_to_9_window_key = Disabled
s0_rotate_to_10_window_key = Disabled
s0_rotate_to_11_window_key = Disabled
s0_rotate_to_12_window_key = Disabled

[place]
s0_workarounds = true
s0_mode = 2
s0_multioutput_mode = 0
s0_force_placement_match = 
s0_position_matches = 
s0_position_x_values = 
s0_position_y_values = 
s0_position_constrain_workarea = 
s0_mode_matches = 
s0_mode_modes = 
s0_viewport_matches = 
s0_viewport_x_values = 
s0_viewport_y_values = 

[workarounds]
s0_keep_minimized_windows = false
s0_legacy_fullscreen = false
s0_firefox_menu_fix = false
s0_ooo_menu_fix = true
s0_notification_daemon_fix = false
s0_java_fix = true
s0_java_taskbar_fix = true
s0_qt_fix = false
s0_convert_urgency = false
s0_aiglx_fragment_fix = true
s0_fglrx_xgl_fix = false
s0_force_glx_sync = false
s0_no_wait_for_video_sync = false
s0_force_swap_buffers = false
s0_sticky_alldesktops = false
s0_alldesktop_sticky_match = any

[resizeinfo]
s0_fade_time = 500
s0_always_show = false
s0_text_color = #000000ff
s0_gradient_1 = #cccce6cc
s0_gradient_2 = #f3f3f3cc
s0_gradient_3 = #d9d9d9cc

[ring]
s0_next_key = <Super>Tab
s0_next_button = Disabled
s0_prev_key = <Shift><Super>Tab
s0_prev_button = Disabled
s0_next_all_key = <Alt><Super>Tab
s0_next_all_button = Disabled
s0_prev_all_key = <Shift><Alt><Super>Tab
s0_prev_all_button = Disabled
s0_next_group_key = Disabled
s0_next_group_button = Disabled
s0_prev_group_key = Disabled
s0_prev_group_button = Disabled
s0_speed = 1.500000
s0_timestep = 1.200000
s0_inactive_opacity = 100
s0_window_match = Normal | Dialog | ModalDialog | Utility | Unknown
s0_overlay_icon = 1
s0_darken_back = true
s0_minimized = true
s0_select_with_mouse = false
s0_ring_clockwise = false
s0_ring_width = 70
s0_ring_height = 60
s0_thumb_width = 350
s0_thumb_height = 250
s0_min_brightness = 0.500000
s0_min_scale = 0.400000
s0_window_title = true
s0_title_font_bold = false
s0_title_font_size = 16
s0_title_back_color = #00000099
s0_title_font_color = #ffffffff
s0_title_text_placement = 0

[clone]
s0_initiate_button = <Shift><Super>Button1

[fade]
s0_fade_mode = 0
s0_fade_speed = 5.000000
s0_fade_time = 100
s0_window_match = any & !(title=notify-osd)
s0_visual_bell = false
s0_fullscreen_visual_bell = false
s0_dim_unresponsive = true
s0_unresponsive_brightness = 65
s0_unresponsive_saturation = 0

[grid]
s0_put_center_key = <Control><Alt>KP_5
s0_put_left_key = <Control><Alt>KP_4
s0_put_right_key = <Control><Alt>KP_6
s0_put_top_key = <Control><Alt>KP_8
s0_put_bottom_key = <Control><Alt>KP_2
s0_put_topleft_key = <Control><Alt>KP_7
s0_put_topright_key = <Control><Alt>KP_9
s0_put_bottomleft_key = <Control><Alt>KP_1
s0_put_bottomright_key = <Control><Alt>KP_3
s0_put_maximize_key = <Control><Alt>KP_0
s0_put_restore_key = <Control><Alt>r
s0_top_left_corner_action = 4
s0_top_edge_action = 10
s0_top_right_corner_action = 6
s0_left_edge_action = 4
s0_right_edge_action = 6
s0_bottom_left_corner_action = 4
s0_bottom_edge_action = 0
s0_bottom_right_corner_action = 6
s0_snapoff_maximized = false
s0_snapback_windows = true
s0_left_edge_threshold = 15
s0_right_edge_threshold = 15
s0_top_edge_threshold = 20
s0_bottom_edge_threshold = 5
s0_draw_indicator = true
s0_outline_color = #fb8b009f
s0_fill_color = #fb8b004f

[staticswitcher]
s0_next_button = Disabled
s0_next_key = <Alt>Tab
s0_prev_button = Disabled
s0_prev_key = <Shift><Alt>Tab
s0_next_all_button = Disabled
s0_next_all_key = <Control><Alt>Tab
s0_prev_all_button = Disabled
s0_prev_all_key = <Shift><Control><Alt>Tab
s0_next_group_button = Disabled
s0_next_group_key = Disabled
s0_prev_group_button = Disabled
s0_prev_group_key = Disabled
s0_next_no_popup_button = Disabled
s0_next_no_popup_key = Disabled
s0_prev_no_popup_button = Disabled
s0_prev_no_popup_key = Disabled
s0_next_panel_button = Disabled
s0_next_panel_key = Disabled
s0_prev_panel_button = Disabled
s0_prev_panel_key = Disabled
s0_speed = 4.000000
s0_timestep = 1.200000
s0_window_match = Normal | Dialog | Toolbar | Utility | Unknown
s0_minimized = true
s0_auto_change_vp = true
s0_popup_delay = 0.200000
s0_mouse_select = true
s0_saturation = 100
s0_brightness = 100
s0_opacity = 100
s0_icon = true
s0_icon_only = false
s0_mipmap = false
s0_row_align = 1
s0_focus_on_switch = false
s0_bring_to_front = false
s0_highlight_mode = 0
s0_highlight_rect_hidden = 1
s0_highlight_color = #00000096
s0_highlight_border_color = #000000c8
s0_highlight_border_inlay_color = #c8c8c8c8

[winrules]
s0_skiptaskbar_match = 
s0_skippager_match = 
s0_above_match = 
s0_below_match = 
s0_sticky_match = 
s0_fullscreen_match = 
s0_maximize_match = 
s0_no_argb_match = 
s0_no_move_match = 
s0_no_resize_match = 
s0_no_minimize_match = 
s0_no_maximize_match = 
s0_no_close_match = 
s0_no_focus_match = 
s0_size_matches = 
s0_size_width_values = 
s0_size_height_values = 

[colorfilter]
s0_toggle_window_key = <Super>f
s0_toggle_screen_key = <Super>d
s0_switch_filter_key = <Control><Super>s
s0_filters = negative;negative-green;blueish-filter;sepia;grayscale;deuteranopia;protanopia;
s0_filter_decorations = false
s0_filter_match = any
s0_exclude_match = type=Desktop

[commands]
s0_command0 = 
s0_command1 = 
s0_command2 = 
s0_command3 = 
s0_command4 = 
s0_command5 = 
s0_command6 = 
s0_command7 = 
s0_command8 = 
s0_command9 = 
s0_command10 = 
s0_command11 = 
s0_command12 = 
s0_command13 = 
s0_command14 = 
s0_command15 = 
s0_command16 = 
s0_command17 = 
s0_command18 = 
s0_command19 = 
s0_command20 = 
s0_run_command0_key = Disabled
s0_run_command1_key = Disabled
s0_run_command2_key = Disabled
s0_run_command3_key = Disabled
s0_run_command4_key = Disabled
s0_run_command5_key = Disabled
s0_run_command6_key = Disabled
s0_run_command7_key = Disabled
s0_run_command8_key = Disabled
s0_run_command9_key = Disabled
s0_run_command10_key = Disabled
s0_run_command11_key = Disabled
s0_run_command12_key = Disabled
s0_run_command13_key = Disabled
s0_run_command14_key = Disabled
s0_run_command15_key = Disabled
s0_run_command16_key = Disabled
s0_run_command17_key = Disabled
s0_run_command18_key = Disabled
s0_run_command19_key = Disabled
s0_run_command20_key = Disabled
s0_run_command0_button = Disabled
s0_run_command1_button = Disabled
s0_run_command2_button = Disabled
s0_run_command3_button = Disabled
s0_run_command4_button = Disabled
s0_run_command5_button = Disabled
s0_run_command6_button = Disabled
s0_run_command7_button = Disabled
s0_run_command8_button = Disabled
s0_run_command9_button = Disabled
s0_run_command10_button = Disabled
s0_run_command11_button = Disabled
s0_run_command12_button = Disabled
s0_run_command13_button = Disabled
s0_run_command14_button = Disabled
s0_run_command15_button = Disabled
s0_run_command16_button = Disabled
s0_run_command17_button = Disabled
s0_run_command18_button = Disabled
s0_run_command19_button = Disabled
s0_run_command20_button = Disabled
s0_run_command0_edge = 
s0_run_command1_edge = 
s0_run_command2_edge = 
s0_run_command3_edge = 
s0_run_command4_edge = 
s0_run_command5_edge = 
s0_run_command6_edge = 
s0_run_command7_edge = 
s0_run_command8_edge = 
s0_run_command9_edge = 
s0_run_command10_edge = 
s0_run_command11_edge = 
s0_run_command12_edge = 
s0_run_command13_edge = 
s0_run_command14_edge = 
s0_run_command15_edge = 
s0_run_command16_edge = 
s0_run_command17_edge = 
s0_run_command18_edge = 
s0_run_command19_edge = 
s0_run_command20_edge = 

[core]
s0_active_plugins = core;composite;opengl;copytex;decor;move;compiztoolbox;resize;regex;place;clone;grid;animation;zoom;put;wobbly;cube;switcher;rotate;ring;unityshell;
s0_audible_bell = true
s0_ignore_hints_when_maximized = true
s0_hide_skip_taskbar_windows = true
s0_edge_delay = 0
s0_ping_delay = 5000
s0_default_icon = icon
s0_do_serialize = false
s0_overlapping_outputs = 0
s0_detect_outputs = true
s0_outputs = 640x480+0+0;
s0_click_to_focus = true
s0_raise_on_click = true
s0_autoraise = true
s0_autoraise_delay = 1000
s0_focus_prevention_level = 1
s0_focus_prevention_match = !(class=Polkit-gnome-authentication-agent-1)
s0_close_window_key = <Alt>F4
s0_close_window_button = Disabled
s0_raise_window_key = Disabled
s0_raise_window_button = <Control>Button6
s0_lower_window_key = Disabled
s0_lower_window_button = <Alt>Button6
s0_minimize_window_key = <Alt>F9
s0_minimize_window_button = Disabled
s0_maximize_window_key = <Alt>F10
s0_unmaximize_window_key = <Alt>F5
s0_maximize_window_horizontally_key = Disabled
s0_maximize_window_vertically_key = Disabled
s0_window_menu_key = <Alt>space
s0_window_menu_button = <Alt>Button3
s0_show_desktop_key = <Control><Alt>d
s0_show_desktop_edge = 
s0_toggle_window_maximized_key = Disabled
s0_toggle_window_maximized_button = Disabled
s0_toggle_window_maximized_horizontally_key = Disabled
s0_toggle_window_maximized_vertically_key = Disabled
s0_toggle_window_shaded_key = <Control><Alt>s
s0_hsize = 4
s0_vsize = 4
s0_number_of_desktops = 4

[animation]
s0_open_effects = animation:Glide 2;animation:None;animation:Fade;
s0_open_durations = 120;80;80;
s0_open_matches = ((type=Normal | Unknown) | name=sun-awt-X11-XFramePeer | name=sun-awt-X11-XDialogPeer) & !(role=toolTipTip | role=qtooltip_label) & !(type=Normal & override_redirect=1) & !(name=gnome-screensaver);(type=Menu | PopupMenu | DropdownMenu | Combo | Dialog | ModalDialog | Normal);(type=Tooltip | Notification | Utility) & !(name=compiz) & !(title=notify-osd);
s0_open_options = ;;;
s0_open_random_effects = 
s0_close_effects = animation:Glide 2;animation:Fade;animation:None;
s0_close_durations = 120;80;50;
s0_close_matches = ((type=Normal | Unknown) | name=sun-awt-X11-XFramePeer | name=sun-awt-X11-XDialogPeer) & !(role=toolTipTip | role=qtooltip_label) & !(type=Normal & override_redirect=1) & !(name=gnome-screensaver) & !(name=gnome-screenshot);(type=Menu | PopupMenu | DropdownMenu | Combo | Dialog | ModalDialog | Normal);(type=Tooltip | Notification | Utility) & !(name=compiz) & !(title=notify-osd);
s0_close_options = ;;;
s0_close_random_effects = 
s0_minimize_effects = animation:Zoom;
s0_minimize_durations = 220;
s0_minimize_matches = (type=Normal | Dialog | ModalDialog | Unknown);
s0_minimize_options = ;
s0_minimize_random_effects = 
s0_shade_effects = animation:Roll Up;
s0_shade_durations = 300;
s0_shade_matches = (type=Normal | Dialog | ModalDialog | Utility | Unknown);
s0_shade_options = ;
s0_shade_random_effects = 
s0_focus_effects = animation:Fade;
s0_focus_durations = 150;
s0_focus_matches = (type=Normal | Dialog | ModalDialog | Utility | Unknown) & !(name=compiz);
s0_focus_options = ;
s0_all_random = false
s0_time_step = 16
s0_curved_fold_amp_mult = 1.000000
s0_curved_fold_zoom_to_taskbar = true
s0_dodge_mode = 1
s0_dodge_gap_ratio = 0.500000
s0_dream_zoom_to_taskbar = true
s0_glide1_away_position = 1.000000
s0_glide1_away_angle = 0.000000
s0_glide1_zoom_to_taskbar = false
s0_glide2_away_position = -0.100000
s0_glide2_away_angle = 0.000000
s0_glide2_zoom_to_taskbar = true
s0_horizontal_folds_amp_mult = 1.000000
s0_horizontal_folds_num_folds = 3
s0_horizontal_folds_zoom_to_taskbar = true
s0_magic_lamp_moving_end = true
s0_magic_lamp_grid_res = 100
s0_magic_lamp_open_start_width = 30
s0_magic_lamp_wavy_moving_end = true
s0_magic_lamp_wavy_grid_res = 100
s0_magic_lamp_wavy_max_waves = 3
s0_magic_lamp_wavy_amp_min = 200.000000
s0_magic_lamp_wavy_amp_max = 300.000000
s0_magic_lamp_wavy_open_start_width = 30
s0_rollup_fixed_interior = false
s0_sidekick_num_rotations = 0.500000
s0_sidekick_springiness = 0.000000
s0_sidekick_zoom_from_center = 0
s0_wave_width = 0.700000
s0_wave_amp_mult = 1.000000
s0_zoom_from_center = 0
s0_zoom_springiness = 0.080000

[zoom]
s0_initiate_button = <Super>Button3
s0_zoom_in_button = <Super>Button4
s0_zoom_out_button = <Super>Button5
s0_zoom_pan_button = <Super>Button2
s0_speed = 1.500000
s0_timestep = 1.200000
s0_zoom_factor = 2.000000
s0_filter_linear = false

[mousepoll]
s0_mouse_poll_interval = 40

[thumbnail]
s0_thumb_size = 200
s0_show_delay = 100
s0_border = 16
s0_thumb_color = #0000007f
s0_fade_speed = 0.500000
s0_current_viewport = true
s0_always_on_top = true
s0_window_like = true
s0_mipmap = false
s0_title_enabled = true
s0_font_bold = true
s0_font_size = 12
s0_font_color = #000000ff

[annotate]
s0_initiate_free_draw_button = <Alt><Super>Button1
s0_initiate_line_button = <Alt><Super>Button2
s0_initiate_rectangle_button = <Shift><Alt><Super>Button1
s0_initiate_ellipse_button = <Shift><Alt><Super>Button2
s0_erase_button = <Alt><Super>Button3
s0_clear_key = <Alt><Super>k
s0_clear_button = Disabled
s0_draw_shapes_from_center = true
s0_fill_color = #ff000088
s0_stroke_color = #00ff00ff
s0_erase_width = 20.000000
s0_stroke_width = 3.000000
```

---

### Post by ventrical on 2011-09-25
> **effenberg0x0 said:**
> Have you ever had any success with the flatfile backend? It always crashed for me (save, create, export, import, whatever).

Regards
Effenberg

I was able to save a profile with the flatfile backend. (I think it was a wrong thing not to include defaults) and it destroyed Unity 3D!! :)

I'm  back at it.

:)

---

### Post by ventrical on 2011-09-25
I'm going to work on this problem on another machine. In the meantime, can someone please remind me how to get my Unity 3D desktop back! :)

I already tried : unity --reset

---

### Post by VinDSL on 2011-09-25
> **ventrical said:**
> I'm going to work on this problem on another machine. In the meantime, can someone please remind me how to get my Unity 3D desktop back! :)

I already tried : unity --reset
Hrm...

In this case, I would reinstall CCSM. ;)

---

### Post by ventrical on 2011-09-25
> **VinDSL said:**
> Hrm...

In this case, I would reinstall CCSM. ;)

Thanks Vin.  I'll try that with synaptic, try to import that saved file that I have and report back here.

---

### Post by ventrical on 2011-09-25
!!Yessiree!! That worked as usual.!! :) Just remember to tic the Unity Plug-in while logged into Unity 2D!!

Thanks again Vin!

 Now I am going to try and see if I can load that *.profile.

---

### Post by ventrical on 2011-09-25
> **effenberg0x0 said:**
> Have you ever had any success with the flatfile backend? It always crashed for me (save, create, export, import, whatever).

Regards
Effenberg

OK... I was able to export and save and then  - after some work - import the saved file and got  the cube and all my settings.

To rotate the cube you have to press <crtl+alt+left-mouse-key> ..etc..

 After uninstalling and re-installing ccsm I had to hard reboot.

  So for me thats good news because I can save  different compiz profiles without having to  pic through them on the GUI.

---

### Post by effenberg0x0 on 2011-09-25
Hey guys, 

Yep, that is the profile flatfile. Generally I have so many crashes when I try to play with ccsm preferences that I can never get to this file. 

My idea is this: Once we have working defaut settings in the flatfile format, and supposing the flatfile backend works for import and load, it will probably be much more more reliable and less buggy than the current gconf backend, which is broken for a long time. The wait / reset problem, the disappearing window decoration problem, the missing switcher/panel (unity plugin disabled) complains would be dealt with nicely. 

Again, assuming the flatfile way works beter than gconf right now, we can easily host a defaults flatfile somewhere and direct users to wget / install it with a small 10-lines bash script. This would help users temporarily, until compiz, ccsm and gconf people get their stuff together. It could, be a deb in a ppa, etc.

Regards,
Effenberg

---

### Post by ventrical on 2011-09-25
It escapes me at the moment but there was a member who put up a gconf file before downloading ccsm. If I  find it I'll post the link.

@effenberg .... great idea!

---

### Post by mc4man on 2011-09-25
One thing to keep in mind though not that applicable in the context here - 
Many of the plugins that were previously installed by default have now been split out to "compiz-plugins" which ATM is not part of the default install
(compiz-plugins is installed as a recommend of ccsm

---

### Post by ventrical on 2011-09-25
Atm?

---

### Post by mc4man on 2011-09-25
> **ventrical said:**
> Atm?

At the moment

---

### Post by ventrical on 2011-09-25
#-o

:)

---

### Post by ventrical on 2011-09-25
Ok .. found it. I can only get that back-end tool to work somewhat stable  on an install that I prepped  before installing compiz by doing exactly the following -

thanks to words of wisdom from mc4man

> **mc4man said:**
> Myself use cube/rotate rather than wall (unity requies either wall or cube be set.
On any fresh install rather than mess with ccsm I start with this  command, after compiz resets then go in and set up # of ws's, scroll on  desktop, adjust the text overlay on the scale spread,  ect. (I remove  quite a # of plugins that aren't useful here
```
gconftool-2 -s --type=list --list-type=string  /apps/compiz-1/general/screen0/options/active_plugins   "[core,composite,opengl,decor,png,text,vpswitch,resize,place,cube,gnomecompat,move,regex,rotate,scale,scaleaddon,animation,expo,unityshell]"
```There  is an erronous conflict between cube> flip left & unity >  edge reveal left, though recently unity seems to take it a bit  personally at times and the launcher can suddenly stop revealing on left  edge.
(can be fixed by disabling the reveal & flip, then re-enabling both

Till the 2nd part of the minimize bug has a fix released - xserver was  fix released today, unity will be next upgrade, it important to make  sure the in unity plugin > switcher > that "show minimized windows  in switcher" option remains disabled

---

### Post by ventrical on 2011-09-25
That 'preference' setting in ccsm is like a cat (Ocelot) on a hot tin roof!!!! Iv'e busted three installs but I can only get it to work on one. Acer Extensa 4420 .. but otherwise I have a reasonbale fascimile of compiz working for now.

  Thats a tough cat to skin.  Where angels fear to tread sort of stuff...

---

### Post by VinDSL on 2011-09-25
> **ventrical said:**
> That 'preference' setting in ccsm is like a cat (Ocelot) on a hot tin roof!!![...]

Thats a tough cat to skin.  Where angels fear to tread sort of stuff...
It's all good fun, right?  Like playing with nitroglycerin...  LoL!  :D

---

### Post by effenberg0x0 on 2011-09-25
Oh f... I can't even look at ccsm preferences without it crashing. I'll have to get back to you on that later... Gonna try something on a fresh VM... seriously pissed right now

Regards,
Effenberg

---

### Post by Utew on 2011-09-25
Same here..it's so touchy at this point, that I don't even dare to open CCSM. It's caused me to do a unity --reset a few times today. Hope this gets ironed out soon, as it's tremendously frustrating. Luckily it doesn't affect GS. 

Ah, the joys of beta testing. ;)

---

### Post by ventrical on 2011-09-26
> **VinDSL said:**
> It's all good fun, right?  Like playing with nitroglycerin...  LoL!  :D

Sure is Vin..:)  fun and all- but it makes me wonder why such a simple process as saving those preferences would cause that app to go completely bonkers and have such a wide-spread effect on the whole system and I am tempted to assume that this also could big a big security flaw... but we need bugs like these  :)

I know we have GNOME 3 , falllback and other DE's but I am try to use compiz to build a (scroll-o-dex) concept desktop pseudo environment. Without compiz working right , it's really tough - so I have had to backstep to lucid.

  But all seriousness aside.. I'm not bellyaching :) beta testing Oneiric is a real experience for Linux Immersion !!

:)

---

### Post by ventrical on 2011-09-26
Good news is that changes made to additional users who have admin privlidges does not affect other users who already have  running compiz profile - meaning to say if ccsm somehow foobarrs a session on a logged on user then that system can be recovered by following the steps suggested in this forum (reset --unity)(uninstall - reinstall compiz) and the other users can be logged on to and they will not be affect by broken system. It certainly is a strange phenomenon because I thought ccsm was global for all users.

So this provides for some breathing room as an experimenter can create multiple users on their  *system*, each with their own individual profile - not affecting the other users in the groups.

---

### Post by iamnotthemessiah on 2011-09-26
just wanna add that im having this too, and on one occasion unity --reset didnt even work so in the end i ctrl-alt-f1 and deleted ~/.compiz-1 and ~/.config/compiz-1 and rebooted to get it working

in my case the problems seemed to occur when messing with ccsm > place windows > fixed window placement, but i guess its a general ccsm profile thing

and yes its like playing with nitroglyserine. this has to be fixed before release

not a dig at anyone but compiz was rock stable for years until canonical touched it/unity

---

### Post by ventrical on 2011-09-26
> **iamnotthemessiah said:**
> just wanna add that im having this too, and on one occasion unity --reset didnt even work so in the end i ctrl-alt-f1 and deleted ~/.compiz-1 and ~/.config/compiz-1 and rebooted to get it working

in my case the problems seemed to occur when messing with ccsm > place windows > fixed window placement, but i guess its a general ccsm profile thing

and yes its like playing with nitroglyserine. this has to be fixed before release

not a dig at anyone but compiz was rock stable for years until canonical touched it/unity


 I have been experimenting with some of the overall bindings (macros) that intergrate Unity into compiz and I am assuming that there are some sideXside floating macros that are causing some of the erractic behaviour - and also  other traffic cops along the bus that threads the two together.

  One key is the <super> or <Windows Icon> key. How ironic eh ? I am experimenting - for example- changing the <super> for  Unity-Launcher from <windows icon> to <u> for unity> and so far so good. Also some keys   for some compiz features can be replaced with other bindings - especially free up the <alt> and <ctrl> keys because these triggers are heavily depended upon by other depends and here is where may lay the ACPI  sideXside.

---

### Post by ventrical on 2011-09-28
Recent updates of most compiz packs have really smoothed it out for my nVidia  graphics.

I'm about to try preferences.

---

### Post by effenberg0x0 on 2011-09-28
I agree. I have been enabling / disabling plugins, applying regexp exceptions, etc today with rare crashes. NVidia GTS450 with proprietary 280.13 driver. I really lost it last time I was messing with it. CCSM hates me.

There's something weird about Video/Compiz & VirtualBox thou... 


Regards,
Effenberg

---

### Post by VinDSL on 2011-09-28
> **ventrical said:**
> I'm about to try preferences.
Heh!  Light the fuse and RUN!!!  :D

BTW, Opera-Next was updated today too.  My system is running much smoother, overall, now.

These (100s and 100s) of updates are starting to have a positive affect.

---

### Post by ventrical on 2011-09-28
> **VinDSL said:**
> Heh!  Light the fuse and RUN!!!  :D

BTW, Opera-Next was updated today too.  My system is running much smoother, overall, now.

These (100s and 100s) of updates are starting to have a positive affect.

Yep.. I hear ya... :)  I was able to export/save a profile no problem and most of the plugin-extras are working too..

uummmmm.. yep .. I am about to ask you  a question about graphics drivers.  I bet your busy .. but here goes.

How do I install the Nouveau driver for nVidia GEForce 218/512MB. I ran jockey and only get three drivers.. current (recommended) current (most recent) and binary.

  When I run jockey on the laptop with ATI graphic it tells me nothing. My graphics are working great .. I just want to see if it gets hot like the others are having problems with.\\thanks

---

### Post by iamnotthemessiah on 2011-09-28
still as rotten as before here :(

---

### Post by effenberg0x0 on 2011-09-28
@Ventrical

Dude, I just answered your question about NVidia drivers in the other thread ([http://ubuntuforums.org/showthread.php?p=11293922#post11293922](http://ubuntuforums.org/showthread.php?p=11293922#post11293922)), check there. Whatever you do, DO NOT tell Jockey to install drivers for you. This thing is seriously broken, you'll boot to no GUI and have to reinstall drivers again. No matter if you have drivers installed or not, it continuously advice you to install nvidia-current, glx, vdpau, etc. I broke some PCs these days by trying it (uninstalled Jockey).

Regards,
Effenberg

---

### Post by ventrical on 2011-09-28
Ok.. thanks effenberg.. on my way to check it out.

Heres a short compiz demo on my nvidia GT218

[http://www.youtube.com/watch?v=lachoU4I6zc](http://www.youtube.com/watch?v=lachoU4I6zc)

---

### Post by effenberg0x0 on 2011-09-28
Very cool man, visibly a good performance. 

Although I believe I'd have a seizure in less than 10 minutes :)

But, don't get me wrong, it is exciting. This is desktop is something to play with after some vodka. Like WOW, the flying spreadsheet is torching the swirling firefox. Hope this crazy angry flying apps don't mess with those beautiful, peaceful and colorful gears. Aw, that was close. Leave'em alone!! 

Regards,
Effenberg

---

### Post by ventrical on 2011-09-28
Thanks .. actually I was trying to bust it :)

heaheahehaeh

---

### Post by iamnotthemessiah on 2011-09-28
dont know if this is common knowledge or not but about 8 hours ago i installed xubuntu-desktop and chose xubuntu at the login prompt. in xubuntu the compiz unity plugin is disabled by default. everything compiz works perfectly, every compiz/ccsm problem is the unity plugin. every problem lies within the unity plugin 100% for sure

---

