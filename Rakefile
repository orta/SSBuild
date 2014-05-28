# encoding: UTF-8
#
# SSBuild. Get you an iOS app!
#

class String
    def self.colorize(text, color_code)
        "\e[#{color_code}m#{text}\e[0m"
    end

    def cyan
        self.class.colorize(self, 36)
    end

    def green
        self.class.colorize(self, 32)
    end
  
    def red
        self.class.colorize(self, 31)      
    end
end

desc 'Unlocks the keychain.'
def unlock_keychain(keychain_loc, password)
    puts "Unlocking Keychain".cyan
    `/usr/bin/security list-keychains -s #{keychain_loc}`
    `/usr/bin/security default-keychain -d user -s #{keychain_loc}`
    `/usr/bin/security unlock-keychain -p #{password} #{keychain_loc}` 
    `/usr/bin/security set-keychain-settings -t 3600 -l #{keychain_loc}` 
end

desc 'Extracts a UUID from a provisioning profile'
def uuid_from_profile(profile)
    uuid_str = `grep UUID -A1 -a #{profile}`
    uuid = uuid_str.match(/[-A-Z0-9]{36}/)[0]
    return uuid
end
