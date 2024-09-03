# Build System

## Introduction
Build system (or buildsys for short) is a python package that performs the following operations:
1. Uses edalize under the hood to generate build scripts for RTL IP. It can generate this for simulation and vivado.
2. Generate code (C++, python and SV) for register read/writes (AXI-LITE) - (What this will end up being is TBD. This might be its own package. We shall call it `Autocode`.)
3. Should be used as a git submodule

## Specifications

buildsys.py takes in the following arguments when called from the command line
1. `context` - Can target specific `context` like different boards, cocotb, vunit
2. `top` - Top level IP or App. The context will dictate what file will be taken in as top. For instance if we have a block called "blk" and the context is a board or vivado. Then top level will be blk.sv else it will be tb_blk.sv
3. `config` - This dictates what *YAML* file will get picked up for manifesting. It assumes a `manifest_<config>.toml` file in the script directory under IP or App that you are targetting.
