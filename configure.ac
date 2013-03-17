dnl Process this file with autoconf to produce a configure script.

AC_INIT(mstflint, 3.0, orenk@mellanox.co.il)

AC_DEFINE_UNQUOTED([PROJECT], ["mstflint"], [Define the project name.])
AC_SUBST([PROJECT])

AC_DEFINE_UNQUOTED([VERSION], ["3.0"], [Define the project version.])
AC_SUBST([VERSION])

AC_CONFIG_AUX_DIR(config)
AC_CONFIG_SRCDIR([README])
AM_INIT_AUTOMAKE(mstflint, 3.0)

dnl Checks for programs
AC_PROG_CC
AC_PROG_CXX
AC_PROG_LIBTOOL
AC_CONFIG_HEADERS( config.h )

AC_MSG_CHECKING(--enable-dc argument)
AC_ARG_ENABLE(dc,
		    [  --disable-dc            Disable mstflint "dc" command. Eliminate zlib dependency],
		    [enable_dc=$enableval],
		    [enable_dc="yes"])
AC_MSG_RESULT($enableval)
if test "$enable_dc" = "yes"; then
  AC_CHECK_HEADER(zlib.h,,AC_MSG_ERROR([cannot find zlib.h . Use --disable-dc to remove this dependaency]))
  AC_CHECK_LIB(z, uncompress,, AC_MSG_ERROR([cannot find zlib uncompress() function. Use --disable-dc to remove this dependaency]))
  mstflint_LIBS="-lz"
else
  mstflint_CXXFLAGS="-DNO_ZLIB"  
fi
AC_SUBST(mstflint_LIBS)
AC_SUBST(mstflint_CXXFLAGS)

AC_CONFIG_FILES( mstflint.spec )

AC_OUTPUT( Makefile dev_mgt/Makefile mflash/Makefile flint/Makefile small_utils/Makefile ) 