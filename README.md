<h1 align="center">
  A'tuin
</h1>
<blockquote align="center">
  Through the fathomless deeps of space swims the star turtle Great A’Tuin, bearing on its back the four giant elephants who carry on their shoulders the mass of the Discworld.
 </blockquote>

<p align="center">
  <a href="https://github.com/ellie/atuin/actions?query=workflow%3ARust"><img src="https://img.shields.io/github/workflow/status/ellie/atuin/Rust?style=flat-square" /></a>
  <a href="https://crates.io/crates/atuin"><img src="https://img.shields.io/crates/v/atuin.svg?style=flat-square" /></a>
  <a href="https://crates.io/crates/atuin"><img src="https://img.shields.io/crates/d/atuin.svg?style=flat-square" /></a>
  <a href="https://github.com/ellie/atuin/blob/main/LICENSE"><img src="https://img.shields.io/crates/l/atuin.svg?style=flat-square" /></a>
</p>
 
A'tuin manages and synchronizes your shell history! Instead of storing
everything in a text file (such as ~/.history), A'tuin uses a sqlite database.
While being a little more complex, this allows for more functionality.

As well as the expected command, A'tuin stores

- duration
- exit code
- working directory
- hostname
- time
- a unique session ID

## Install

### AUR
A'tuin is available on the [AUR](https://aur.archlinux.org/packages/atuin/)
```
yay -S atuin # or your AUR helper of choice
```

### With cargo
`atuin` needs a nightly version of Rust + Cargo! It's best to use
[rustup](https://rustup.rs/) for getting set up there.

```
rustup default nightly

cargo install atuin
```

### From source
```
rustup default nightly
git clone https://github.com/ellie/atuin.git
cd atuin
cargo install --path .
```

### Shell plugin
Once the binary is installed, the shell plugin requires installing:

zplug:

```
zplug "ellie/atuin", at:main
```

otherwise, clone the repo and `source /path/to/repo/atuin.plugin.zsh` in your `.zshrc`

## Usage

By default A'tuin will rebind ctrl-r to use fzf to fuzzy search your history. You
can specify a different fuzzy tool by changing the value of `ATUIN_FUZZY`:

```
export ATUIN_FUZZY=fzy
```

### Import history

```
atuin import auto # detect shell, then import

or

atuin import zsh  # specify shell
```

### List history

```
atuin history list
```

### Stats

A'tuin can calculate statistics for a single day, and accepts "natural language" style date input, as well as absolute dates:

```
$ atuin stats day last friday

+---------------------+------------+
| Statistic           | Value      |
+---------------------+------------+
| Most used command   | git status |
+---------------------+------------+
| Commands ran        |        450 |
+---------------------+------------+
| Unique commands ran |        213 |
+---------------------+------------+

$ atuin stats day 01/01/21 # also accepts absolute dates
```

It can also calculate statistics for all of known history:

```
$ atuin stats all

+---------------------+-------+
| Statistic           | Value |
+---------------------+-------+
| Most used command   |    ls |
+---------------------+-------+
| Commands ran        |  8190 |
+---------------------+-------+
| Unique commands ran |  2996 |
+---------------------+-------+
```

## ...what's with the name?

A'tuin is named after "The Great A'tuin", a giant turtle from Terry Pratchett's
Discworld series of books.