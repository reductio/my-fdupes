# Building fdupes on Fedora Linux

This project uses the GNU Autotools build system. To compile the development
version you will need to generate the `configure` script first and have several
dependencies installed.

## Install Dependencies

Use Fedora's package manager to install build tools and optional libraries:

```bash
sudo dnf install gcc make autoconf automake pkgconfig \
    ncurses-devel pcre2-devel sqlite-devel
```

The `ncurses` and `pcre2` libraries enable the screen-mode interface introduced
in fdupes 2.0.0.  SQLite is used for the file signature database.  You may omit
these packages and disable the features with the `--without-*` configure
options described below.

## Generate Build Files

If a `configure` script is not present (as is the case when cloning the
repository directly), run:

```bash
autoreconf --install
```

This step creates the `configure` script and related files required for
compilation.

## Configure and Compile

From the project directory run:

```bash
./configure
make
```

These steps compile the program using the default options.  You may disable
optional features with flags such as `--without-ncurses` or `--without-sqlite`:

```bash
./configure --without-ncurses
```

followed by `make` as before.

## Installation

To install the resulting binary and manual pages under `/usr/local` run:

```bash
sudo make install
```

You can change the installation prefix by passing `--prefix=/path` to
`configure` before running `make install`.

