# h-e-l-l-o-w-o-r-l-d

An unnecessary-ily long build pipeline for a hello world program

# Build

Only dependency you need is `docker-compose`<br/>
Run `./build.sh` to build the entire pipeline

## Clean

Run `./build.sh clean` to clean all build related files

## Run

Run `./build.sh run` to run the `hello_world` executable created by `./build.sh`

## Shell (for debugging)

Run `./build.sh shell` to start a shell in the container where `./build.sh` is run

# Setup

## Tools

<!-- Add an entry here for every sub project -->
- `build_tools`: Zig library that gets compiled into a python module; used in `src/build.py` to execute bash statements
- `PATH`: C executable that transpiles [PATH](https://esolangs.org/wiki/PATH) to C
- `hello_world.c_maker`: PATH file that, when transpiled to c and compiled, will make the final `hello_world.c`

## Pipeline

<!-- Add an entry here for every step in the build process -->
- Build `tools` python module
  - `src/build_tools`
  - See `start-build.sh`

- Compile PATH to C transpiler
  - `src/PATH`
  - See `build.py`, `src/PATH/Makefile`

- Compile `hello_world.c_maker`
  - `src/hello_world.c_maker`
  - `hello_world.c_maker.PATH` -> `hello_world.c_maker.c` -> `hello_world.c_maker`
  - Uses PATH to C transpiler
  - See `build.py`, `src/hello_world.c_maker/build.sh`

- Compile `hello_world`
  - `hello_world.c_maker` -> `hello_world.c` -> `hello_world`
  - See `build.py`

# Contributing

If you wish to contribute to this project, you're free to do so,
just fork the repository, do your changes, open a pull request,
and if your changes are good (they make the build time longer), we'll merge it

Also please make sure to do the following<br/>
1) Add necessary commands to `src/build.py` (or `src/start-build.sh`)
2) Add any intermediate files to `.gitignore` and `src/clean.sh`
3) Keep documentation up to date (mainly this [README.md](README.md))

## What to contribute, what not to

What we want is not you just going
> heh, I'll just add the `gcc` source code to this and compile that, then it'll take a couple minutes at least

We want something more creative, something that was built *specifically* for this project, specifically to make *it* build slower

## DISCLAIMER

By contributing to this project, you agree to license the code you wrote for this project under the [Unlisence](LICENSE)<br/>
Or in other words, anyone is allowed to do whatever they want with your code
