load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

http_archive(
    name = "aspect_rules_js",
    sha256 = "ad666b12324bab8bc151772bb2eff9aadace7bfd4d624157c2ac3931860d1c95",
    strip_prefix = "rules_js-1.11.1",
    url = "https://github.com/aspect-build/rules_js/archive/refs/tags/v1.11.1.tar.gz",
)

http_archive(
    name = "aspect_rules_ts",
    sha256 = "e81f37c4fe014fc83229e619360d51bfd6cb8ac405a7e8018b4a362efa79d000",
    strip_prefix = "rules_ts-1.0.4",
    url = "https://github.com/aspect-build/rules_ts/archive/refs/tags/v1.0.4.tar.gz",
)

http_archive(
    name = "aspect_rules_swc",
    sha256 = "2c979b07bc665a9db376ee80ac31278bbb5e11776f9f076e16abd0eabe8f9ae5",
    strip_prefix = "rules_swc-0.20.0",
    url = "https://github.com/aspect-build/rules_swc/archive/refs/tags/v0.20.0.tar.gz",
)

http_archive(
    name = "aspect_bazel_lib",
    sha256 = "be236556c7b9c7b91cb370e837fdcec62b6e8893408cd4465ae883c9d7c67024",
    strip_prefix = "bazel-lib-1.18.0",
    url = "https://github.com/aspect-build/bazel-lib/archive/refs/tags/v1.18.0.tar.gz",
)

http_archive(
    name = "aspect_rules_esbuild",
    sha256 = "f9b5bf16251e3e4e127337ef968e6a398c9a4f353f1730e6c7ff6c9a8981e858",
    strip_prefix = "rules_esbuild-0.13.4",
    url = "https://github.com/aspect-build/rules_esbuild/archive/refs/tags/v0.13.4.tar.gz",
)

load("@aspect_bazel_lib//lib:repositories.bzl", "aspect_bazel_lib_dependencies")

aspect_bazel_lib_dependencies()

load("@aspect_rules_js//js:repositories.bzl", "rules_js_dependencies")

rules_js_dependencies()

load("@aspect_rules_ts//ts:repositories.bzl", "rules_ts_dependencies", TS_LATEST_VERSION = "LATEST_VERSION")

rules_ts_dependencies(ts_version = TS_LATEST_VERSION)

load("@aspect_rules_esbuild//esbuild:dependencies.bzl", "rules_esbuild_dependencies")

rules_esbuild_dependencies()

load("@rules_nodejs//nodejs:repositories.bzl", "DEFAULT_NODE_VERSION", "nodejs_register_toolchains")

nodejs_register_toolchains(
    name = "nodejs",
    node_version = DEFAULT_NODE_VERSION,
)

load("@aspect_rules_js//npm:npm_import.bzl", "npm_translate_lock")

npm_translate_lock(
    name = "npm",
    pnpm_lock = "//:pnpm-lock.yaml",
    verify_node_modules_ignored = "//:.bazelignore",
    warn_on_unqualified_tarball_url = True,
)

load("@npm//:repositories.bzl", "npm_repositories")

npm_repositories()

load("@aspect_rules_swc//swc:dependencies.bzl", "rules_swc_dependencies")

rules_swc_dependencies()

load("@aspect_rules_swc//swc:repositories.bzl", "swc_register_toolchains", SWC_LATEST_VERSION = "LATEST_VERSION")

swc_register_toolchains(
    name = "swc",
    swc_version = SWC_LATEST_VERSION,
)

load("@aspect_rules_esbuild//esbuild:repositories.bzl", "esbuild_register_toolchains", ESBUILD_LATEST_VERSION = "LATEST_VERSION")

esbuild_register_toolchains(
    name = "esbuild",
    esbuild_version = ESBUILD_LATEST_VERSION,
)
