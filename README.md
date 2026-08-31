# syn-vault

A password-locked folder for your own files. Open it and it is a normal
directory at `~/Vaults/<name>`; close it and what is left on disk is
encrypted.

gocryptfs does the encryption. This program does not invent any of its own —
it makes vaults, opens and closes them, and gives that a window and a command
line.

## Using it

```bash
syn-vault create private      # make one, and set its password
syn-vault open private        # unlocked at ~/Vaults/private
syn-vault list                # the vaults, and which are open
syn-vault close private       # locked again
syn-vault gui                 # the window
```

The encrypted files live in `~/.local/share/syn-vault/<name>.vault` and are
readable only while the vault is open.

## What it will not do

**Nothing anywhere keeps a second copy of the password.** A vault whose
password is lost is lost with it. There is no recovery key and no reset.

A password is never passed on a command line, so it cannot appear in a
process list or a shell history. Opening a vault over a directory that
already has files in it is refused rather than silently hiding them.

## Requires

`gocryptfs` and `fuse3`, both of which do the actual work. `quickshell` for
the window. With `synfiles` installed, a vault can be opened from the file
manager.

## Install

```bash
git clone https://github.com/velle999/syn-vault
cd syn-vault && makepkg -si
```

makepkg fetches the source for this PKGBUILD's exact version from this
repository's releases, so a clone can only ever build the source it was
written against. `.SRCINFO` lists what it needs.

## Where this comes from

Developed in [the SynapseOS monorepo](https://github.com/velle999/SYNAPSE),
in `syn-vault/`. **This repository is generated from it** — the PKGBUILD, a
generated `.SRCINFO` and this README — so issues and patches belong there.

syn-vault 0.1.0-5 · GPL-2.0-or-later
