dnl Process this file with autoconf to produce a configure script.

AC_INIT(configure.ac)
AM_INIT_AUTOMAKE(gcalctool, 5.29.92)
AM_CONFIG_HEADER(config.h)
AM_MAINTAINER_MODE
GNOME_MAINTAINER_MODE_DEFINES
m4_ifdef([AM_SILENT_RULES],[AM_SILENT_RULES([yes])])

AC_ISC_POSIX
AC_PROG_CC
AM_PROG_CC_STDC
AC_HEADER_STDC

AM_GCONF_SOURCE_2

GNOME_COMPILE_WARNINGS(yes)

dnl ###########################################################################
dnl Dependencies
dnl ###########################################################################

GTK_REQUIRED=2.18
GCONF_REQUIRED=1.1.9

PKG_CHECK_MODULES(GCALCTOOL, [
    gtk+-2.0 >= $GTK_REQUIRED
    gconf-2.0 >= $GCONF_REQUIRED
    gio-2.0
    libxml-2.0
    gmodule-export-2.0
])

PKG_CHECK_MODULES(GCALCCMD, [
    glib-2.0
])

AC_CHECK_LIB(m, log)

dnl ###########################################################################
dnl Determine if a usable lex is available on this system
dnl ###########################################################################

AM_PROG_LEX
if [[ "$LEX" != "flex" ]]; then
	AC_MSG_ERROR(flex is required to create the gcalctool scanners)
fi

dnl ###########################################################################
dnl Determine if a usable yacc is available on this system
dnl ###########################################################################

AC_PROG_YACC
AC_CHECK_PROG(HAVE_YACC, $YACC, yes, no)
if [[ "$HAVE_YACC" = "no" ]]; then
	AC_MSG_ERROR($YACC is not usable as yacc - consider using bison)
fi

dnl ###########################################################################
dnl Internationalization
dnl ###########################################################################

IT_PROG_INTLTOOL([0.35.0])
GETTEXT_PACKAGE=gcalctool
AC_SUBST(GETTEXT_PACKAGE)
AM_GLIB_GNU_GETTEXT

dnl ###########################################################################
dnl Documentation
dnl ###########################################################################

GNOME_DOC_INIT

dnl ###########################################################################
dnl Files to generate
dnl ###########################################################################

AC_OUTPUT([
Makefile
src/Makefile
po/Makefile.in
data/Makefile
help/Makefile
])