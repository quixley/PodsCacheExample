# Uncomment the next line to define a global platform for your project
# platform :ios, '9.0'

def is_pod_binary_cache_enabled
  true
end

if is_pod_binary_cache_enabled
  plugin 'cocoapods-binary-cache'
  config_cocoapods_binary_cache(
    cache_repo: {
      "default" => {
        "remote" => "https://github.com/bigbangvn/demo-pod-binary-cache-prebuilt-libs.git",
        "local" => "~/.cocoapods-binary-cache/PodBinaryCacheExample-libs"
      }
    },
    prebuild_config: "Debug",
    dev_pods_enabled: true
  )
  # set_unbuilt_dev_pods(['ConfigSDK']) // To test ABI breaking (crash, call wrong function) when there're code change in ConfigSDK and don't rebuild it's clients (ConfigService)
end

def binary_pod(name, *args)
  if is_pod_binary_cache_enabled
    pod name, args, :binary => true
  else
    pod name, args
  end
end

target 'PodsCacheExample' do
  # Comment the next line if you don't want to use dynamic frameworks
  use_frameworks!

  # Pods for PodsCacheExample
  binary_pod 'SDWebImage'
  binary_pod 'Alamofire'
end
