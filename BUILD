load("@rules_python//python:defs.bzl", "py_runtime")
load("@rules_python//python:defs.bzl", "py_runtime_pair")
load("@rules_python//python:defs.bzl", "py_binary")

sh_binary(
    name = "wrapped_python",
    srcs = [":python3_wrapper.sh"],
    data = [":python3_data.sh"],
)

py_runtime(
    name = "python3_runtime",
    interpreter = ":wrapped_python",
    python_version = "PY3",
)

py_runtime_pair(
    name = "python3_runtime_pair",
    py2_runtime = None,
    py3_runtime = ":python3_runtime",
)

toolchain(
    name = "python3_toolchain",
    toolchain = ":python3_runtime_pair",
    toolchain_type = "@bazel_tools//tools/python:toolchain_type",
)

py_binary(
    name = "test",
    srcs = [":test.py"],
)
