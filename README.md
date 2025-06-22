package com.example;

import org.bukkit.Bukkit;
import org.bukkit.ChatColor;
import org.bukkit.event.EventHandler;
import org.bukkit.event.Listener;
import org.bukkit.event.player.PlayerMoveEvent;
import org.bukkit.plugin.java.JavaPlugin;

public class AntiCheatPlugin extends JavaPlugin implements Listener {

    @Override
    public void onEnable() {
        Bukkit.getPluginManager().registerEvents(this, this);
        getLogger().info("AntiCheatPlugin has been enabled!");
    }

    @Override
    public void onDisable() {
        getLogger().info("AntiCheatPlugin has been disabled!");
    }

    @EventHandler
    public void onPlayerMove(PlayerMoveEvent event) {
        double speed = event.getFrom().distance(event.getTo());
        if (speed > 0.5) { // Giới hạn tốc độ di chuyển
            event.getPlayer().sendMessage(ChatColor.RED + "You are moving too fast! This action has been logged.");
            // Thực hiện hành động như kick hoặc cảnh báo
            // event.getPlayer().kickPlayer("Speed hacking detected!");
        }
    }
}
