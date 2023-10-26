cargo build --target=wasm32-unknown-unknown --release --target-dir=wasm
- TypeError: WebAssembly.instantiate(): Imports argument must be present and must be an object
- 在尝试实例化WebAssembly模块时，缺少了必要的导入对象。当一个WebAssembly模块有外部依赖（例如，它需要从JavaScript环境中导入某些功能）时，这些依赖需要在实例化时提供。
- const importObject = {
  env: {
    // 这里列出了所有需要从JavaScript导入到WebAssembly的函数
  }
};
- 使用wasm-bindgen：如果您使用Rust编写的WebAssembly模块，并使用wasm-bindgen工具，那么它会为您生成一个JavaScript包装器，这个包装器会自动处理所有的导入和导出。

WebAssembly.instantiate(wasmModule, importObject).then(instance => {
  // 使用WebAssembly实例
});


wasm-pack build --target web --out-dir web

wasm-pack build --target bundler --out-dir bundler
