---
title: "Is it bad coding style?"
date: 2012-08-15
forum: Programming Talk
---

### Post by t1497f35 on 2012-08-15
Hi,
I'm browsing thru some code and it contains a pile of "tmp" named vars of different types.
Have a look, is it a good coding style? Any good reason to use that many "tmp" (non mnemonic) names?
Just wondering.

[PHP]
static gboolean main_window_change_background_timeout_cb (MainWindow* self) {
    gboolean result = FALSE;
    gchar* new_background_file = NULL;
    gboolean _tmp0_ = FALSE;
    MenuBar* _tmp1_;
    gboolean _tmp2_;
    gboolean _tmp3_;
    gboolean _tmp5_;
    Background* _tmp11_;
    const gchar* _tmp12_;
    g_return_val_if_fail (self != NULL, FALSE);
    _tmp1_ = self->priv->menubar;
    _tmp2_ = menu_bar_get_high_contrast (_tmp1_);
    _tmp3_ = _tmp2_;
    if (_tmp3_) {
        _tmp0_ = TRUE;
    } else {
        gboolean _tmp4_ = FALSE;
        _tmp4_ = ug_settings_get_boolean (UG_SETTINGS_KEY_DRAW_USER_BACKGROUNDS);
        _tmp0_ = !_tmp4_;
    }
    _tmp5_ = _tmp0_;
    if (_tmp5_) {
        _g_free0 (new_background_file);
        new_background_file = NULL;
    } else {
        UserList* _tmp6_;
        UserEntry* _tmp7_;
        UserEntry* _tmp8_;
        const gchar* _tmp9_;
        gchar* _tmp10_;
        _tmp6_ = self->user_list;
        _tmp7_ = user_list_get_selected_entry (_tmp6_);
        _tmp8_ = _tmp7_;
        _tmp9_ = _tmp8_->background;
        _tmp10_ = g_strdup (_tmp9_);
        _g_free0 (new_background_file);
        new_background_file = _tmp10_;
    }
    _tmp11_ = self->priv->background;
    _tmp12_ = new_background_file;
    background_set_current_background (_tmp11_, _tmp12_);
    self->priv->change_background_timeout = (guint) 0;
    result = FALSE;
    _g_free0 (new_background_file);
    return result;
}
[/PHP]

---

### Post by satsujinka on 2012-08-15
The usage of "tmp" is most certainly a bad idea. Aside from making it hard to tell what's going on, it also makes it really hard to tell if you have duplicates or unnecessary variables. At the very least, tmp2, tmp4, tmp8, tmp10, and tmp12 aren't actually being used for anything.

Also you seem to be freeing (I assume _g_free0 is a free wrapper) new_background_file even though it starts as NULL and if tmp5 you proceed to set it back to NULL (you do set it to something useful otherwise though.)

---

### Post by trent.josephsen on 2012-08-15
It's awful. Not only because of multiple variables (of *different types*, no less!) with meaningless names, but because they start with underscores. On top of that, no comments!

If I had to guess... was this code machine generated?

---

### Post by QIII on 2012-08-15
Oh, c'mon.

Who needs to write code so that it can be maintained by some poor schmoe that gets it dropped in his lap when you go to Cozumel for a month?

Sheesh!

---

### Post by t1497f35 on 2012-08-15
Thanks anyone, it's actually code from unity-greeter, which I guess was written by folks from Canonical.

---

### Post by QIII on 2012-08-15
Someone needs to be spanked and sent to bed without supper!

---

